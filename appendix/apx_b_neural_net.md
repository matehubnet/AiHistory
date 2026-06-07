# 附录B：从零实现一个神经网络

用Python和NumPy手写一个两层神经网络，训练它识别手写数字（MNIST）。不使用任何深度学习框架。

## 网络架构

`
输入(784) → 隐藏层(128, ReLU) → 输出(10, Softmax)
`

## 核心代码

`python
import numpy as np

def relu(z):
    return np.maximum(0, z)

def relu_deriv(z):
    return (z > 0).astype(float)

def softmax(z):
    exp_z = np.exp(z - np.max(z, axis=1, keepdims=True))
    return exp_z / np.sum(exp_z, axis=1, keepdims=True)

def cross_entropy_loss(y_pred, y_true):
    m = y_true.shape[0]
    log_probs = -np.log(y_pred[np.arange(m), y_true] + 1e-8)
    return np.mean(log_probs)

class NeuralNetwork:
    def __init__(self, input_size=784, hidden_size=128, output_size=10):
        self.W1 = np.random.randn(input_size, hidden_size) * 0.01
        self.b1 = np.zeros((1, hidden_size))
        self.W2 = np.random.randn(hidden_size, output_size) * 0.01
        self.b2 = np.zeros((1, output_size))

    def forward(self, X):
        self.z1 = X @ self.W1 + self.b1
        self.a1 = relu(self.z1)
        self.z2 = self.a1 @ self.W2 + self.b2
        self.a2 = softmax(self.z2)
        return self.a2

    def backward(self, X, y, lr=0.1):
        m = X.shape[0]
        # Output layer gradient
        dz2 = self.a2.copy()
        dz2[np.arange(m), y] -= 1
        dz2 /= m
        dW2 = self.a1.T @ dz2
        db2 = np.sum(dz2, axis=0, keepdims=True)
        # Hidden layer gradient (backpropagation!)
        da1 = dz2 @ self.W2.T
        dz1 = da1 * relu_deriv(self.z1)
        dW1 = X.T @ dz1
        db1 = np.sum(dz1, axis=0, keepdims=True)
        # Update weights
        self.W2 -= lr * dW2
        self.b2 -= lr * db2
        self.W1 -= lr * dW1
        self.b1 -= lr * db1

    def train(self, X, y, epochs=10, lr=0.1, batch_size=64):
        for epoch in range(epochs):
            for i in range(0, X.shape[0], batch_size):
                X_batch = X[i:i+batch_size]
                y_batch = y[i:i+batch_size]
                self.forward(X_batch)
                self.backward(X_batch, y_batch, lr)
            pred = self.forward(X).argmax(axis=1)
            acc = (pred == y).mean()
            print(f"Epoch {epoch+1}, Accuracy: {acc:.4f}")
`

## 关键观察

1. forward()做前向传播：输入→线性变换→ReLU→线性变换→Softmax
2. backward()做反向传播：从输出层开始，用链式法则逐层计算梯度
3. dz2是输出层的梯度，dz1是隐藏层的梯度——注意dz1依赖dz2和W2.T，这就是"反向传播"
4. 整个训练循环只有约50行代码，但包含了深度学习的所有核心要素
