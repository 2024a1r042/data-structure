//Implement a Binary Tree using Linked List and develop functions to perform traversal, searching, insertion and deletion operations. 
//29 april 2025
#include <stdio.h>
#include <stdlib.h>

typedef struct TreeNode {
    struct TreeNode* left;
    int data;
    struct TreeNode* right;
} Node;

Node* createNode(int value) {
    Node* node = (Node*)malloc(sizeof(Node));
    node->data = value;
    node->left = node->right = NULL;
    return node;
}

Node* insert(Node* root, int value) {
    if (root == NULL)
        return createNode(value);

    Node* queue[100];
    int front = 0, rear = 0;
    queue[rear++] = root;

    while (front < rear) {
        Node* temp = queue[front++];
        if (temp->left == NULL) {
            temp->left = createNode(value);
            break;
        }
        else if (temp->right == NULL) {
            temp->right = createNode(value);
            break;
        }
        else {
            queue[rear++] = temp->left;
            queue[rear++] = temp->right;
        }
    }
    return root;
}

void preorder(Node* root) {
    if (root == NULL) return;
    printf("%d ", root->data);
    preorder(root->left);
    preorder(root->right);
}

void inorder(Node* root) {
    if (root == NULL) return;
    inorder(root->left);
    printf("%d ", root->data);
    inorder(root->right);
}

void postorder(Node* root) {
    if (root == NULL) return;
    postorder(root->left);
    postorder(root->right);
    printf("%d ", root->data);
}

void levelorder(Node* root) {
    if (root == NULL) return;
    Node* queue[100];
    int front = 0, rear = 0;
    queue[rear++] = root;

    while (front < rear) {
        Node* temp = queue[front++];
        printf("%d ", temp->data);
        if (temp->left != NULL) queue[rear++] = temp->left;
        if (temp->right != NULL) queue[rear++] = temp->right;
    }
}

Node* search(Node* root, int value) {
    if (root == NULL) return NULL;
    Node* queue[100];
    int front = 0, rear = 0;
    queue[rear++] = root;

    while (front != rear) {
        Node* temp = queue[front++];
        if (temp->data == value) return temp;
        if (temp->left != NULL) queue[rear++] = temp->left;
        if (temp->right != NULL) queue[rear++] = temp->right;
    }
    return NULL;
}

Node* findDeepest(Node* root) {
    if (root == NULL) return NULL;

    Node* queue[100];
    int front = 0, rear = 0;
    queue[rear++] = root;
    Node* temp = NULL;
    Node* lastParent = NULL;

    while (front != rear) {
        lastParent = temp;
        temp = queue[front++];
        if (temp->left != NULL) queue[rear++] = temp->left;
        if (temp->right != NULL) queue[rear++] = temp->right;
    }

    if (lastParent != NULL) {
        if (lastParent->left == temp) lastParent->left = NULL;
        else if (lastParent->right == temp) lastParent->right = NULL;
    }

    return temp;
}

Node* deleteNode(Node* root, int value) {
    if (root == NULL) return NULL;

    Node* temp = search(root, value);
    if (temp == NULL) {
        printf("Element not found!!\n");
        return root;
    }
    Node* deepest = findDeepest(root);
    if (deepest != NULL) {
        temp->data = deepest->data;
        free(deepest);
    }
    return root;
}

int main() {
    int choice, val;
    Node* root = NULL;

    while (1) {
        printf("1. Insert\n");
        printf("2. Pre-order\n");
        printf("3. In-order\n");
        printf("4. Post-order\n");
        printf("5. Level-order\n");
        printf("6. Search\n");
        printf("7. Delete\n");
        printf("8. Exit\n");
        printf("Enter Choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value to insert: ");
                scanf("%d", &val);
                root = insert(root, val);
                break;
            case 2:
                preorder(root);
                printf("\n");
                break;
            case 3:
                inorder(root);
                printf("\n");
                break;
            case 4:
                postorder(root);
                printf("\n");
                break;
            case 5:
                levelorder(root);
                printf("\n");
                break;
            case 6:
                printf("Enter value to search: ");
                scanf("%d", &val);
                {
                    Node* found = search(root, val);
                    if (found) printf("Node found with value: %d\n", found->data);
                    else printf("Node not found.\n");
                }
                break;
            case 7:
                printf("Enter value to delete: ");
                scanf("%d", &val);
                root = deleteNode(root, val);
                break;
            case 8:
                exit(0);
            default:
                printf("Invalid choice!!\n");
        }
        printf("\n");
    }
    return 0;
}
