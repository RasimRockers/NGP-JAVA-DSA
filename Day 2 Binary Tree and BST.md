

#🔸 1. Binary Tree in Java

A **Binary Tree** is a tree where each node has **at most two children**, usually referred to as `left` and `right`.

### ✅ Basic Binary Tree Code in Java

```java
class Node {
    int data;
    Node left, right;

    public Node(int value) {
        data = value;
        left = right = null;
    }
}

class BinaryTree {
    Node root;

    // Inorder traversal (Left -> Root -> Right)
    void inorderTraversal(Node node) {
        if (node == null)
            return;

        inorderTraversal(node.left);
        System.out.print(node.data + " ");
        inorderTraversal(node.right);
    }

    // Preorder traversal (Root -> Left -> Right)
    void preorderTraversal(Node node) {
        if (node == null)
            return;

        System.out.print(node.data + " ");
        preorderTraversal(node.left);
        preorderTraversal(node.right);
    }

    // Postorder traversal (Left -> Right -> Root)
    void postorderTraversal(Node node) {
        if (node == null)
            return;

        postorderTraversal(node.left);
        postorderTraversal(node.right);
        System.out.print(node.data + " ");
    }

    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();
        tree.root = new Node(10);
        tree.root.left = new Node(5);
        tree.root.right = new Node(20);
        tree.root.left.left = new Node(3);
        tree.root.left.right = new Node(7);

        System.out.println("Inorder traversal:");
        tree.inorderTraversal(tree.root);
    }
}
```

---

# 🔸 2. Binary Search Tree (BST) in Java

A **BST** is a type of binary tree where:

* Left child has value **less than** the parent.
* Right child has value **greater than** the parent.

### ✅ BST Implementation in Java

```java
class BSTNode {
    int data;
    BSTNode left, right;

    public BSTNode(int value) {
        data = value;
        left = right = null;
    }
}

class BinarySearchTree {
    BSTNode root;

    // Insert a value
    BSTNode insert(BSTNode node, int value) {
        if (node == null) {
            return new BSTNode(value);
        }

        if (value < node.data) {
            node.left = insert(node.left, value);
        } else if (value > node.data) {
            node.right = insert(node.right, value);
        }

        return node;
    }

    // Inorder traversal (will be sorted in BST)
    void inorder(BSTNode node) {
        if (node == null)
            return;
        inorder(node.left);
        System.out.print(node.data + " ");
        inorder(node.right);
    }

    // Search for a value
    boolean search(BSTNode node, int key) {
        if (node == null)
            return false;

        if (key == node.data)
            return true;
        else if (key < node.data)
            return search(node.left, key);
        else
            return search(node.right, key);
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();
        int[] values = {50, 30, 70, 20, 40, 60, 80};

        for (int val : values) {
            bst.root = bst.insert(bst.root, val);
        }

        System.out.println("Inorder traversal of BST:");
        bst.inorder(bst.root);

        System.out.println("\nSearch 60: " + bst.search(bst.root, 60));
        System.out.println("Search 25: " + bst.search(bst.root, 25));
    }
}
```

---


