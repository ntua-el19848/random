# Perceptron Problem

Ο παρακάτω κώδικας υλοποιεί ένα απλό Perceptron, που είναι ο πιο βασικός τύπος νευρωνικού δικτύου, για δυαδική ταξινόμηση. Παρακάτω είναι μία περιγραφή του Perceptron της άσκησης:

1. **Βασική Λειτουργία:**

    - Ο Perceptron δέχεται δύο χαρακτηριστικά εισόδου (X1, X2)
    - Προσπαθεί να ταξινομήσει τα σημεία σε δύο κλάσεις (+1 ή -1)
    - Χρησιμοποιεί βάρη (w1, w2) και μια μεροληψία (bias) για να κάνει την πρόβλεψη

2. **Διαδικασία Εκπαίδευσης:**

    - Αρχικοποιεί τα βάρη με τυχαίες μικρές τιμές
    - Για κάθε σημείο εκπαίδευσης:

        - Υπολογίζει την πρόβλεψη: sign(w1x1 + w2x2 + bias)
        - Αν η πρόβλεψη είναι λανθασμένη, ενημερώνει τα βάρη και το bias


    - Επαναλαμβάνει μέχρι να μην υπάρχουν λάθη ή να φτάσει τον μέγιστο αριθμό επαναλήψεων


3. **Διαχείριση Δεδομένων:**

    - Διαβάζει τα δεδομένα από αρχεία CSV
    - Αγνοεί την πρώτη γραμμή που περιέχει τις επικεφαλίδες
    - Χωρίζει τα δεδομένα σε χαρακτηριστικά (X1, X2) και ετικέτες (Label)


4. **Αξιολόγηση:**

    - Υπολογίζει την ακρίβεια στα δεδομένα εκπαίδευσης
    - Ελέγχει την απόδοση σε νέα δεδομένα (test data)
    - Εμφανίζει τα τελικά βάρη και το bias του μοντέλου



Η λύση είναι υλοποιημένη σε Python χωρίς τη χρήση εξειδικευμένων βιβλιοθηκών μηχανικής μάθησης (εκτός από το numpy για αριθμητικούς υπολογισμούς).


--- 

## The code

```python
import numpy as np  # numpy is used for efficient numerical operations

class Perceptron:

    # A simple implementation of the Perceptron algorithm for binary classification.
    # The perceptron learns to separate two classes by adjusting weights and bias.
    
    def __init__(self, learning_rate=0.1, max_iterations=1000):
        # Initialize the perceptron with learning parameters.
        # Args:
        #     learning_rate (float): How much to adjust weights on each error (between 0 and 1)
        #     max_iterations (int): Maximum number of times to iterate through training data
        self.learning_rate = learning_rate
        self.max_iterations = max_iterations
        self.weights = None  # Will store the feature weights (w1, w2)
        self.bias = None     # Will store the bias term (b)
        
    def initialize_weights(self, n_features):
        # Initialize weights and bias to small random values.
        # Small random values are better than zeros as starting points.
        # Args:
        #     n_features (int): Number of input features (2 in this case: X1, X2)

        # Initialize weights with small random values (multiplied by 0.01 to keep them small)
        self.weights = np.random.randn(n_features) * 0.01
        self.bias = np.random.randn() * 0.01
    
    def predict_single(self, x):
        # Predict class for a single input using the perceptron formula:
        # f(x) = sign(w·x + b)
        # where w is the weight vector, x is the input vector, and b is the bias
        # Args:
        #     x (numpy.array): Input feature vector [X1, X2]
        # Returns:
        #     int: 1 if activation >= 0, -1 otherwise

        # Calculate the dot product of weights and input features, then add bias
        activation = np.dot(x, self.weights) + self.bias
        # Apply the sign function: return 1 if activation >= 0, else -1
        return 1 if activation >= 0 else -1
    
    def predict(self, X):
        # Predict classes for multiple inputs.        
        # Args:
        #     X (numpy.array): Matrix of input features, shape (n_samples, n_features)
        # Returns:
        #     numpy.array: Array of predictions (1 or -1 for each input)
        return np.array([self.predict_single(x) for x in X])
    
    def train(self, X, y):
        # Train the perceptron using the perceptron learning algorithm.
        
        # The algorithm:
        # 1. For each training example:
        #     - Make a prediction
        #     - If prediction is wrong:
        #         * Update weights: w = w + learning_rate * y * x
        #         * Update bias: b = b + learning_rate * y
        # 2. Repeat until no errors or max iterations reached
        # Args:
        #     X (numpy.array): Training features, shape (n_samples, n_features)
        #     y (numpy.array): Training labels (1 or -1 for each sample)

        # Initialize weights if not already done
        if self.weights is None:
            self.initialize_weights(X.shape[1])
            
        # Training loop
        for iteration in range(self.max_iterations):
            misclassified = 0  # Counter for misclassified points in this iteration
            
            # Iterate through all training examples
            for xi, yi in zip(X, y):
                prediction = self.predict_single(xi)
                
                # Update weights and bias if prediction is wrong
                if prediction != yi:
                    # Calculate the update value
                    update = self.learning_rate * yi
                    # Update each weight: w_new = w_old + learning_rate * y * x
                    self.weights += update * xi
                    # Update bias: b_new = b_old + learning_rate * y
                    self.bias += update
                    misclassified += 1
            
            # If no misclassifications, we've found a solution
            if misclassified == 0:
                print(f"Converged after {iteration + 1} iterations")
                break
                
    def accuracy(self, X, y):
        # Calculate classification accuracy (percentage of correct predictions).
        # Args:
        #     X (numpy.array): Input features
        #     y (numpy.array): True labels            
        # Returns:
        #     float: Accuracy score between 0 and 1
        predictions = self.predict(X)
        return np.mean(predictions == y)  # Calculate percentage of correct predictions

def load_data(filename):
    # Load data from a CSV file and separate features and labels.
    # Expected CSV format:
    # X1,X2,Label
    # where X1 and X2 are real numbers and Label is either 1 or -1
    # Args:
    #     filename (str): Path to the CSV file 
    # Returns:
    #     tuple: (X, y) where X is features array and y is labels array

    data = np.loadtxt(filename, delimiter=',', skiprows=1)  # Load CSV file
    X = data[:, :2] # First two columns (X1, X2) are features
    y = data[:, 2]   # Last column is the label (1 or -1)
    return X, y

# Main execution block
if __name__ == "__main__":
    # Step 1: Load training data
    print("⏳ Loading training data...")
    X_train, y_train = load_data('training_data.csv')
    
    # Step 2: Create and train perceptron
    print("🎓 Creating and training perceptron...")
    perceptron = Perceptron(learning_rate=0.1, max_iterations=1000)
    perceptron.train(X_train, y_train)
    
    # Step 3: Calculate and display training accuracy
    train_accuracy = perceptron.accuracy(X_train, y_train)
    print(f"\n🎯 Training accuracy: {train_accuracy:.2%}")
    
    # Step 4: Evaluate on test data
    print("\n🔎 Evaluating on test data...")
    X_test, y_test = load_data('test_data.csv')
    test_accuracy = perceptron.accuracy(X_test, y_test)
    print(f"Test accuracy: {test_accuracy:.2%}")
    
    # Step 5: Display final model parameters
    print("\nFinal model parameters:")
    print(f"Weights (w1, w2): {perceptron.weights}")
    print(f"Bias (b): {perceptron.bias}")
```
---

## Οι έξοδοι του προγράμματος
Παρακάτω φαίνονται screenshots με διαφόρες εκτελέσεις του παραπάνω κώδικα. Παρατηρούμε πως υπάρχει διαφορά από εκτέλεση σε εκτέλεση, τόσο στα τελικά weights όσο και στο τελικό bias. Αυτό συμβαίνει επειδή η αρχικοποίηση των αρχικών βαρών γίνεται με τυχαίες τιμές.

![Screenshot 2025-01-02 225113](https://github.com/user-attachments/assets/f39c5fda-58ae-4c66-b214-89492716b40c)
![Screenshot 2025-01-02 225427](https://github.com/user-attachments/assets/21c88d6a-f044-43dd-b907-3a3159293c8a)
![Screenshot 2025-01-02 225454](https://github.com/user-attachments/assets/f05bb97d-f1cc-43ba-a895-b762b2c1449c)


