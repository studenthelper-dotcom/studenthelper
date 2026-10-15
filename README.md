Slip 1Q.1) Binary Search in a Sorted Array
#include <stdio.h>
int main() {
    int arr[100], n, i, key, low, high, mid;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter %d elements in ascending order:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    printf("Enter element to search: ");
    scanf("%d", &key);

    low = 0;
    high = n - 1;
    while (low <= high) {
        mid = (low + high) / 2;
        if (arr[mid] == key) {
            printf("Element %d found at position %d (Index %d).\n", key, mid + 1, mid);
            return 0;
        } else if (arr[mid] < key) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    printf("Element %d not found in the array.\n", key);
    return 0;
}
Q.2) Static Stack of Integers (Push, Pop, Display)   C
#include <stdio.h>
#define MAX 5
int stack[MAX], top = -1;
void push() {
    int val;
    if (top == MAX - 1) {
        printf("Stack Overflow!\n");
    } else {
        printf("Enter value to push: ");
        scanf("%d", &val);
        stack[++top] = val;
        printf("%d pushed to stack.\n", val);
    }
}
void pop() {
    if (top == -1) {
        printf("Stack Underflow!\n");
    } else {
        printf("Popped element: %d\n", stack[top--]);
    }
}
void display() {
    if (top == -1) {
        printf("Stack is empty.\n");
    } else {
        printf("Stack elements (top to bottom): ");
        for (int i = top; i >= 0; i--) {
            printf("%d ", stack[i]);
        }
        printf("\n");
    }
}
int main() {
    int choice;
    do {
        printf("\n1. Push  2. Pop  3. Display  4. Exit\nEnter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1: push(); break;
            case 2: pop(); break;
            case 3: display(); break;
            case 4: break;
            default: printf("Invalid choice!\n");
        }
    } while (choice != 4);
    return 0;
}

Slip 2Q.1) Bubble Sort in Ascending Order   C
#include <stdio.h>
int main() {
    int a[100], n, i, j, temp;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (a[j] > a[j + 1]) {
                temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }
    printf("Sorted elements in ascending order:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", a[i]);
    }
    printf("\n");
    return 0;
}

Q.2) Singly Linked List with Insert, Delete, and Display   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *head = NULL;
void insert(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = head;
    head = newNode;
    printf("Inserted %d\n", val);
}
void deleteNode(int val) {
    struct Node *temp = head, *prev = NULL;
    if (temp != NULL && temp->data == val) {
        head = temp->next;
        free(temp);
        printf("Deleted %d\n", val);
        return;
    }
    while (temp != NULL && temp->data != val) {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL) {
        printf("Element %d not found!\n", val);
        return;
    }
    prev->next = temp->next;
    free(temp);
    printf("Deleted %d\n", val);
}
void display() {
    struct Node* ptr = head;
    printf("Linked List: ");
    while (ptr != NULL) {
        printf("%d -> ", ptr->data);
        ptr = ptr->next;
    }
    printf("NULL\n");
}
int main() {
    insert(30);
    insert(20);
    insert(10);
    display();
    deleteNode(20);
    display();
    return 0;
}

Slip 3   Q.1) Insertion Sort      C#include <stdio.h>
int main() {
    int a[100], n, i, j, key;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }
    for (i = 1; i < n; i++) {
        key = a[i];
        j = i - 1;
        while (j >= 0 && a[j] > key) {
            a[j + 1] = a[j];
            j--;
        }
        a[j + 1] = key;
    }
    printf("Sorted array:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", a[i]);
    }
    printf("\n");
    return 0;
}

Q.2) Linear Queue Operations (Insert, Delete, Display)      C
#include <stdio.h>
#define SIZE 5
int queue[SIZE], front = -1, rear = -1;
void insert(int val) {
    if (rear == SIZE - 1) {
        printf("Queue Overflow!\n");
    } else {
        if (front == -1) front = 0;
        queue[++rear] = val;
        printf("Inserted %d\n", val);
    }
}
void deleteQ() {
    if (front == -1 || front > rear) {
        printf("Queue Underflow!\n");
    } else {
        printf("Deleted %d\n", queue[front++]);
        if (front > rear) front = rear = -1;
    }
}
void display() {
    if (front == -1 || front > rear) {
        printf("Queue is empty.\n");
    } else {
        printf("Queue elements: ");
        for (int i = front; i <= rear; i++) {
            printf("%d ", queue[i]);
        }
        printf("\n");
    }
}
int main() {
    insert(10);
    insert(20);
    insert(30);
    display();
    deleteQ();
    display();
    return 0;
}

Slip 4Q.1) Linear Search for a Character in an Array   C
#include <stdio.h>
int main() {
    int n, i;
    char arr[100], key;
    printf("Enter number of characters: ");
    scanf("%d", &n);
    printf("Enter %d characters:\n", n);
    for (i = 0; i < n; i++) {
        scanf(" %c", &arr[i]);
    }
    printf("Enter character to search: ");
    scanf(" %c", &key);
    for (i = 0; i < n; i++) {
        if (arr[i] == key) {
            printf("Character '%c' found at index %d (Position %d).\n", key, i, i + 1);
            return 0;
        }
    }
    printf("Character '%c' not found.\n", key);
    return 0;
}

Q.2) Circular Queue (Insert, Delete, Display)   C
#include <stdio.h>
#define SIZE 5
int cqueue[SIZE], front = -1, rear = -1;
void insert(int val) {
    if ((front == 0 && rear == SIZE - 1) || ((rear + 1) % SIZE == front)) {
        printf("Circular Queue Overflow!\n");
        return;
    }
    if (front == -1) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }
    cqueue[rear] = val;
    printf("Inserted %d\n", val);
}
void deleteCQ() {
    if (front == -1) {
        printf("Circular Queue Underflow!\n");
        return;
    }
    printf("Deleted %d\n", cqueue[front]);
    if (front == rear) {
        front = rear = -1;
    } else {
        front = (front + 1) % SIZE;
    }
}
void display() {
    if (front == -1) {
        printf("Circular Queue is empty.\n");
        return;
    }
    printf("Circular Queue elements: ");
    int i = front;
    while (1) {
        printf("%d ", cqueue[i]);
        if (i == rear) break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}
int main() {
    insert(10);
    insert(20);
    insert(30);
    display();
    deleteCQ();
    display();
    return 0;
}

Slip 5Q.1) Reverse a String using Stack   C
#include <stdio.h>
#include <string.h>
#define MAX 100
int main() {
    char str[MAX], stack[MAX];
    int top = -1, i;
    printf("Enter a string: ");
    scanf("%99s", str);
    for (i = 0; str[i] != '\0'; i++) {
        stack[++top] = str[i];
    }
    printf("Reversed string: ");
    while (top >= 0) {
        printf("%c", stack[top--]);
    }
    printf("\n");
    return 0;
}

Q.2) Binary Search Tree (Insert, In-order Traversal, Count Leaf & Non-Leaf Nodes)   (Covers both Q.2 and the OR question on Slip 5 & Slip 11)   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node *left, *right;
};
struct Node* createNode(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->left = newNode->right = NULL;
    return newNode;
}
struct Node* insert(struct Node* root, int val) {
    if (root == NULL) return createNode(val);
    if (val < root->data)
        root->left = insert(root->left, val);
    else if (val > root->data)
        root->right = insert(root->right, val);
    return root;
}
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}
int countLeaf(struct Node* root) {
    if (root == NULL) return 0;
    if (root->left == NULL && root->right == NULL) return 1;
    return countLeaf(root->left) + countLeaf(root->right);
}
int countNonLeaf(struct Node* root) {
    if (root == NULL || (root->left == NULL && root->right == NULL)) return 0;
    return 1 + countNonLeaf(root->left) + countNonLeaf(root->right);
}
int main() {
    struct Node* root = NULL;
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    printf("In-order traversal: ");
    inorder(root);
    printf("\nLeaf nodes: %d\n", countLeaf(root));
    printf("Non-leaf nodes: %d\n", countNonLeaf(root));
    return 0;
}

Slip 6Q.1) Store Square of Elements in Another Array and Display Both   C
#include <stdio.h>
int main() {
    int n, i, a[100], sq[100];
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
        sq[i] = a[i] * a[i];
    }
    printf("Original array: ");
    for (i = 0; i < n; i++) printf("%d ", a[i]);
    printf("\nSquare array:   ");
    for (i = 0; i < n; i++) printf("%d ", sq[i]);
    printf("\n");
    return 0;
}

Q.2) Menu-Driven Singly Linked List (Create, Display, Delete)   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *head = NULL;
void create() {
    int val;
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    printf("Enter value: ");
    scanf("%d", &val);
    newNode->data = val;
    newNode->next = NULL;
    if (head == NULL) {
        head = newNode;
    } else {
        struct Node* temp = head;
        while (temp->next != NULL) temp = temp->next;
        temp->next = newNode;
    }
}
void display() {
    struct Node* temp = head;
    printf("List: ");
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}
void deleteNode() {
    if (head == NULL) {
        printf("List is empty.\n");
        return;
    }
    int val;
    printf("Enter value to delete: ");
    scanf("%d", &val);
    struct Node *temp = head, *prev = NULL;
    if (temp->data == val) {
        head = temp->next;
        free(temp);
        printf("Deleted successfully.\n");
        return;
    }
    while (temp != NULL && temp->data != val) {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL) {
        printf("Element not found.\n");
        return;
    }
    prev->next = temp->next;
    free(temp);
    printf("Deleted successfully.\n");
}
int main() {
    int ch;
    do {
        printf("\n1. Create  2. Display  3. Delete  4. Exit\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1: create(); break;
            case 2: display(); break;
            case 3: deleteNode(); break;
            case 4: break;
            default: printf("Invalid choice!\n");
        }
    } while (ch != 4);
    return 0;
}

Slip 7   Q.1) Find Length of a Linked List      C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *head = NULL;
void insert(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = head;
    head = newNode;
}
void findLength() {
    int count = 0;
    struct Node* temp = head;
    while (temp != NULL) {
        count++;
        temp = temp->next;
    }
    printf("Length of the linked list is: %d\n", count);
}
int main() {
    insert(10);
    insert(20);
    insert(30);
    findLength();
    return 0;
}

Q.2) Convert Infix Expression to Postfix   C
#include <stdio.h>
#include <ctype.h>
char stack[100];
int top = -1;
void push(char x) {
    stack[++top] = x;
}
char pop() {
    if (top == -1) return -1;
    return stack[top--];
}
int priority(char x) {
    if (x == '(') return 0;
    if (x == '+' || x == '-') return 1;
    if (x == '*' || x == '/') return 2;
    if (x == '^') return 3;
    return 0;
}
int main() {
    char exp[100], *e, x;
    printf("Enter the infix expression: ");
    scanf("%s", exp);
    e = exp;
    printf("Postfix expression: ");
    while (*e != '\0') {
        if (isalnum(*e)) {
            printf("%c", *e);
        } else if (*e == '(') {
            push(*e);
        } else if (*e == ')') {
            while ((x = pop()) != '(')
                printf("%c", x);
        } else {
            while (top != -1 && priority(stack[top]) >= priority(*e))
                printf("%c", pop());
            push(*e);
        }
        e++;
    }
    while (top != -1) {
        printf("%c", pop());
    }
    printf("\n");
    return 0;
}

Slip 8Q.1) Static Queue on Integer Data (Insert and Display)   C
#include <stdio.h>
#define MAX 5
int q[MAX], front = -1, rear = -1;
void insert() {
    int val;
    if (rear == MAX - 1) {
        printf("Queue Full!\n");
    } else {
        if (front == -1) front = 0;
        printf("Enter value: ");
        scanf("%d", &val);
        q[++rear] = val;
        printf("Inserted %d\n", val);
    }
}
void display() {
    if (front == -1 || front > rear) {
        printf("Queue Empty.\n");
    } else {
        printf("Queue elements: ");
        for (int i = front; i <= rear; i++) {
            printf("%d ", q[i]);
        }
        printf("\n");
    }
}
int main() {
    insert();
    insert();
    display();
    return 0;
}

Q.2) Doubly Linked List with Insert & Delete   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node *prev, *next;
} *head = NULL;
void insert(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->prev = NULL;
    newNode->next = head;
    if (head != NULL) head->prev = newNode;
    head = newNode;
    printf("Inserted %d\n", val);
}
void deleteNode(int val) {
    struct Node* temp = head;
    while (temp != NULL && temp->data != val) {
        temp = temp->next;
    }
    if (temp == NULL) {
        printf("Element %d not found!\n", val);
        return;
    }
    if (temp->prev != NULL)
        temp->prev->next = temp->next;
    else
        head = temp->next;
    if (temp->next != NULL)
        temp->next->prev = temp->prev;
    free(temp);
    printf("Deleted %d\n", val);
}
void display() {
    struct Node* temp = head;
    printf("Doubly Linked List: ");
    while (temp != NULL) {
        printf("%d <-> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    insert(10);
    insert(20);
    insert(30);
    display();
    deleteNode(20);
    display();
    return 0;
}

Slip 9Q.1) Reverse a Linked List   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *head = NULL;
void insert(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = head;
    head = newNode;
}
void reverse() {
    struct Node *prev = NULL, *current = head, *next = NULL;
    while (current != NULL) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    head = prev;
}
void display() {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}
int main() {
    insert(1);
    insert(2);
    insert(3);
    printf("Original: ");
    display();
    reverse();
    printf("Reversed: ");
    display();
    return 0;
}

Q.2) BST with Insert, Search & Preorder Display   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node *left, *right;
};
struct Node* create(int val) {
    struct Node* node = (struct Node*)malloc(sizeof(struct Node));
    node->data = val;
    node->left = node->right = NULL;
    return node;
}
struct Node* insert(struct Node* root, int val) {
    if (root == NULL) return create(val);
    if (val < root->data)
        root->left = insert(root->left, val);
    else if (val > root->data)
        root->right = insert(root->right, val);
    return root;
}
void preorder(struct Node* root) {
    if (root != NULL) {
        printf("%d ", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}
int search(struct Node* root, int key) {
    if (root == NULL) return 0;
    if (root->data == key) return 1;
    if (key < root->data) return search(root->left, key);
    return search(root->right, key);
}
int main() {
    struct Node* root = NULL;
    root = insert(root, 40);
    insert(root, 20);
    insert(root, 60);
    printf("Preorder: ");
    preorder(root);
    printf("\n");
    if (search(root, 20))
        printf("Element 20 found in BST.\n");
    else
        printf("Not found.\n");
    return 0;
}
Slip 10Q.1) Merge Sort on Initialized Array   C#include <stdio.h>
void merge(int arr[], int l, int m, int r) {
    int i, j, k;
    int n1 = m - l + 1;
    int n2 = r - m;
    int L[n1], R[n2];
    for (i = 0; i < n1; i++) L[i] = arr[l + i];
    for (j = 0; j < n2; j++) R[j] = arr[m + 1 + j];
    i = 0; j = 0; k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) arr[k++] = L[i++];
        else arr[k++] = R[j++];
    }
    while (i < n1) arr[k++] = L[i++];
    while (j < n2) arr[k++] = R[j++];
}
void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}
int main() {
    int A[5] = {87, 30, 44, 20, 51};
    int n = 5;
    mergeSort(A, 0, n - 1);
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) printf("%d ", A[i]);
    printf("\n");
    return 0;
}

Q.2) Menu-Driven Doubly Circular Linked List (Create, Display, Delete at Position)   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node *prev, *next;
} *head = NULL;
void create(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    if (head == NULL) {
        head = newNode;
        head->next = head;
        head->prev = head;
    } else {
        struct Node* last = head->prev;
        last->next = newNode;
        newNode->prev = last;
        newNode->next = head;
        head->prev = newNode;
    }
}
void deleteAtPos(int pos) {
    if (head == NULL || pos <= 0) {
        printf("Invalid operation or empty list.\n");
        return;
    }
    struct Node* temp = head;
    if (pos == 1) {
        if (head->next == head) {
            free(head);
            head = NULL;
            printf("Node deleted.\n");
            return;
        }
        struct Node* last = head->prev;
        head = head->next;
        last->next = head;
        head->prev = last;
        free(temp);
        printf("Node deleted.\n");
        return;
    }
    for (int i = 1; i < pos; i++) {
        temp = temp->next;
        if (temp == head) {
            printf("Position out of range!\n");
            return;
        }
    }
    temp->prev->next = temp->next;
    temp->next->prev = temp->prev;
    free(temp);
    printf("Node deleted.\n");
}
void display() {
    if (head == NULL) {
        printf("List is empty.\n");
        return;
    }
    struct Node* temp = head;
    printf("DCLL: ");
    do {
        printf("%d <-> ", temp->data);
        temp = temp->next;
    } while (temp != head);
    printf("(head)\n");
}
int main() {
    int ch, val, pos;
    do {
        printf("\n1. Create  2. Display  3. Delete at Position  4. Exit\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &val);
                create(val);
                break;
            case 2:
                display();
                break;
            case 3:
                printf("Enter position to delete: ");
                scanf("%d", &pos);
                deleteAtPos(pos);
                break;
            case 4:
                break;
        }
    } while (ch != 4);
    return 0;
}

Slip 11Q.1) Quick Sort on n Random Numbers   C
#include <stdio.h>
#include <stdlib.h>
void swap(int* a, int* b) {
    int t = *a;
    *a = *b;
    *b = t;
}
int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for (int j = low; j <= high - 1; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return (i + 1);
}
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
int main() {
    int n, arr[100];
    printf("Enter number of random elements: ");
    scanf("%d", &n);
    printf("Generated random numbers: ");
    for (int i = 0; i < n; i++) {
        arr[i] = rand() % 100;
        printf("%d ", arr[i]);
    }
    printf("\n");
    quickSort(arr, 0, n - 1);
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) printf("%d ", arr[i]);
    printf("\n");
    return 0;
}

Q.2) Dynamic Stack (Push, Pop, Search)   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *top = NULL;
void push(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = top;
    top = newNode;
    printf("Pushed %d\n", val);
}
void pop() {
    if (top == NULL) {
        printf("Stack Underflow!\n");
        return;
    }
    struct Node* temp = top;
    printf("Popped %d\n", top->data);
    top = top->next;
    free(temp);
}
void search(int key) {
    struct Node* temp = top;
    int pos = 1;
    while (temp != NULL) {
        if (temp->data == key) {
            printf("Element %d found at position %d from top.\n", key, pos);
            return;
        }
        temp = temp->next;
        pos++;
    }
    printf("Element %d not found.\n", key);
}
int main() {
    push(10);
    push(20);
    push(30);
    search(20);
    pop();
    search(30);
    return 0;
}

Slip 12Q.1) Accept Two Polynomials and Display Subtraction   C
#include <stdio.h>
int main() {
    int deg, i, p1[20], p2[20], diff[20];
    printf("Enter highest degree of polynomials: ");
    scanf("%d", &deg);
    printf("Enter coefficients for Polynomial 1 (from x^%d to x^0):\n", deg);
    for (i = deg; i >= 0; i--) {
        printf("Coeff of x^%d: ", i);
        scanf("%d", &p1[i]);
    }
    printf("Enter coefficients for Polynomial 2 (from x^%d to x^0):\n", deg);
    for (i = deg; i >= 0; i--) {
        printf("Coeff of x^%d: ", i);
        scanf("%d", &p2[i]);
        diff[i] = p1[i] - p2[i];
    }
    printf("\nSubtraction Result: ");
    for (i = deg; i >= 0; i--) {
        printf("%dx^%d%s", diff[i], i, (i > 0) ? " + " : "\n");
    }
    return 0;
}

Q.2) Circular Queue (Insert, Delete, Display)   (Use Slip 4 Q.2 above)   
Slip 13 Q.1) Merge Sort on n Elements   (Use Slip 10 Q.1 above; you can prompt for n elements with scanf before calling mergeSort)   
Q.2) Static Linear Queue with Insert(), Delete(), and Length()   C
#include <stdio.h>
#define SIZE 5
int q[SIZE], front = -1, rear = -1;
void insert(int val) {
    if (rear == SIZE - 1) {
        printf("Queue Overflow!\n");
    } else {
        if (front == -1) front = 0;
        q[++rear] = val;
        printf("Inserted %d\n", val);
    }
}
void deleteQ() {
    if (front == -1 || front > rear) {
        printf("Queue Underflow!\n");
    } else {
        printf("Deleted %d\n", q[front++]);
        if (front > rear) front = rear = -1;
    }
}
void length() {
    if (front == -1 || front > rear)
        printf("Total elements in queue: 0\n");
    else
        printf("Total elements in queue: %d\n", rear - front + 1);
}

int main() {
    insert(5);
    insert(10);
    insert(15);
    length();
    deleteQ();
    length();
    return 0;
}

Slip 14Q.1) Search a Given Character using Recursive Binary Search   C
#include <stdio.h>
int binarySearch(char arr[], int low, int high, char key) {
    if (high >= low) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] > key) return binarySearch(arr, low, mid - 1, key);
        return binarySearch(arr, mid + 1, high, key);
    }
    return -1;
}
int main() {
    char arr[] = {'a', 'e', 'i', 'o', 'u'}, key;
    int n = 5;
    printf("Sorted character array: a e i o u\nEnter character to search: ");
    scanf(" %c", &key);
    int result = binarySearch(arr, 0, n - 1, key);
    if (result != -1)
        printf("Character '%c' found at index %d\n", key, result);
    else
        printf("Character '%c' not found\n", key);
    return 0;
}

Q.2) BST with In-Order Display, Total Nodes Count, and Odd Number Count   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node *left, *right;
};
struct Node* create(int val) {
    struct Node* n = (struct Node*)malloc(sizeof(struct Node));
    n->data = val;
    n->left = n->right = NULL;
    return n;
}
struct Node* insert(struct Node* root, int val) {
    if (root == NULL) return create(val);
    if (val < root->data) root->left = insert(root->left, val);
    else if (val > root->data) root->right = insert(root->right, val);
    return root;
}
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}
int countTotal(struct Node* root) {
    if (root == NULL) return 0;
    return 1 + countTotal(root->left) + countTotal(root->right);
}
int countOdd(struct Node* root) {
    if (root == NULL) return 0;
    int isOdd = (root->data % 2 != 0) ? 1 : 0;
    return isOdd + countOdd(root->left) + countOdd(root->right);
}
int main() {
    struct Node* root = NULL;
    root = insert(root, 15);
    insert(root, 10);
    insert(root, 20);
    insert(root, 7);
    printf("In-order traversal: ");
    inorder(root);
    printf("\nTotal nodes in BST: %d\n", countTotal(root));
    printf("Odd numbers count in BST: %d\n", countOdd(root));
    return 0;
}

Slip 15 Q.1) Quick Sort on n Numbers   (Use Slip 11 Q.1 above)   
Q.2) Dynamic Queue Implementation (Insert, Delete, Display)   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *front = NULL, *rear = NULL;
void insert(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = NULL;
    if (rear == NULL) {
        front = rear = newNode;
    } else {
        rear->next = newNode;
        rear = newNode;
    }
    printf("Inserted %d\n", val);
}
void deleteQ() {
    if (front == NULL) {
        printf("Queue Underflow!\n");
        return;
    }
    struct Node* temp = front;
    printf("Deleted %d\n", front->data);
    front = front->next;
    if (front == NULL) rear = NULL;
    free(temp);
}
void display() {
    struct Node* temp = front;
    printf("Queue: ");
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}
int main() {
    insert(100);
    insert(200);
    display();
    deleteQ();
    display();
    return 0;
}

Slip 16Q.1) Sort Character Array using Bubble Sort   C
#include <stdio.h>
int main() {
    char arr[] = {'z', 'a', 'm', 'b', 'k'}, temp;
    int n = 5;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    printf("Sorted characters: ");
    for (int i = 0; i < n; i++) printf("%c ", arr[i]);
    printf("\n");
    return 0;
}

Q.2) Dynamic Circular Queue (Insert, Delete, Display)   (Note: You can also use Slip 7 Q.2 Infix to Postfix for the OR question)   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *front = NULL, *rear = NULL;
void insert(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    if (front == NULL) {
        front = rear = newNode;
        rear->next = front;
    } else {
        rear->next = newNode;
        rear = newNode;
        rear->next = front;
    }
    printf("Inserted %d\n", val);
}
void deleteCQ() {
    if (front == NULL) {
        printf("Queue Underflow!\n");
        return;
    }
    int val = front->data;
    if (front == rear) {
        free(front);
        front = rear = NULL;
    } else {
        struct Node* temp = front;
        front = front->next;
        rear->next = front;
        free(temp);
    }
    printf("Deleted %d\n", val);
}
void display() {
    if (front == NULL) {
        printf("Queue Empty.\n");
        return;
    }
    struct Node* temp = front;
    printf("Dynamic Circular Queue: ");
    do {
        printf("%d -> ", temp->data);
        temp = temp->next;
    } while (temp != front);
    printf("(front)\n");
}
int main() {
    insert(10);
    insert(20);
    insert(30);
    display();
    deleteCQ();
    display();
    return 0;
}

Slip 17Q.1) Sort Array of Structure Customer on custid using Bubble Sort   C
#include <stdio.h>
#include <string.h>
struct Customer {
    int custid;
    char name[30];
    char address[50];
};
int main() {
    struct Customer c[3] = {
        {3, "Amit", "Pune"},
        {1, "Rohan", "Mumbai"},
        {2, "Neha", "Nashik"}
    };
    struct Customer temp;
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2 - i; j++) {
            if (c[j].custid > c[j + 1].custid) {
                temp = c[j];
                c[j] = c[j + 1];
                c[j + 1] = temp;
            }
        }
    }
    printf("Sorted Customers by CustID:\n");
    for (int i = 0; i < 3; i++) {
        printf("ID: %d | Name: %s | Address: %s\n", c[i].custid, c[i].name, c[i].address);
    }
    return 0;
}

Q.2) Check Balanced Parentheses using Stack   C
#include <stdio.h>
#include <string.h>
int main() {
    char exp[100], stack[100];
    int top = -1, flag = 1;
    printf("Enter expression with parentheses: ");
    scanf("%s", exp);
    for (int i = 0; exp[i] != '\0'; i++) {
        if (exp[i] == '(' || exp[i] == '{' || exp[i] == '[') {
            stack[++top] = exp[i];
        } else if (exp[i] == ')' || exp[i] == '}' || exp[i] == ']') {
            if (top == -1) {
                flag = 0;
                break;
            }
            char open = stack[top--];
            if ((exp[i] == ')' && open != '(') ||
                (exp[i] == '}' && open != '{') ||
                (exp[i] == ']' && open != '[')) {
                flag = 0;
                break;
            }
        }
    }
    if (top != -1) flag = 0;
    if (flag) printf("Parentheses are BALANCED.\n");
    else printf("Parentheses are NOT BALANCED.\n");
    return 0;
}

Slip 18Q.1) Display City Code of Corresponding City Name using Linear Search   C
#include <stdio.h>
#include <string.h>
struct city {
    int city_code;
    char name[30];
};
int main() {
    struct city c[3] = {{101, "Pune"}, {102, "Mumbai"}, {103, "Nagpur"}};
    char search_name[30];
    printf("Enter city name to search: ");
    scanf("%s", search_name);
    for (int i = 0; i < 3; i++) {
        if (strcmp(c[i].name, search_name) == 0) {
            printf("City Code for %s: %d\n", c[i].name, c[i].city_code);
            return 0;
        }
    }
    printf("City not found.\n");
    return 0;
}

Q.2) Dynamic Queue with Insert, Length, and Search   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
} *front = NULL, *rear = NULL;
void insert(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = NULL;
    if (rear == NULL) front = rear = newNode;
    else {
        rear->next = newNode;
        rear = newNode;
    }
    printf("Inserted %d\n", val);
}
void length() {
    int count = 0;
    struct Node* temp = front;
    while (temp != NULL) {
        count++;
        temp = temp->next;
    }
    printf("Total elements in queue: %d\n", count);
}
void search(int key) {
    struct Node* temp = front;
    int pos = 1;
    while (temp != NULL) {
        if (temp->data == key) {
            printf("Element %d found at position %d.\n", key, pos);
            return;
        }
        temp = temp->next;
        pos++;
    }
    printf("Element %d not found.\n", key);
}
int main() {
    insert(10);
    insert(20);
    insert(30);
    length();
    search(20);
    return 0;
}

Slip 19Q.1) Create and Display Singly Linked List of Vowels   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    char vowel;
    struct Node* next;
} *head = NULL;
void insert(char v) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->vowel = v;
    newNode->next = head;
    head = newNode;
}
void display() {
    struct Node* temp = head;
    printf("Vowels Linked List: ");
    while (temp != NULL) {
        printf("%c -> ", temp->vowel);
        temp = temp->next;
    }
    printf("NULL\n");
}
int main() {
    insert('u');
    insert('o');
    insert('i');
    insert('e');
    insert('a');
    display();
    return 0;
}

Q.2) BST of char Data (Create, Display, Count Leaf & Non-Leaf Nodes)   C
#include <stdio.h>
#include <stdlib.h>
struct Node {
    char data;
    struct Node *left, *right;
};
struct Node* create(char val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->left = newNode->right = NULL;
    return newNode;
}
struct Node* insert(struct Node* root, char val) {
    if (root == NULL) return create(val);
    if (val < root->data) root->left = insert(root->left, val);
    else if (val > root->data) root->right = insert(root->right, val);
    return root;
}
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%c ", root->data);
        inorder(root->right);
    }
}
int countLeaf(struct Node* root) {
    if (root == NULL) return 0;
    if (root->left == NULL && root->right == NULL) return 1;
    return countLeaf(root->left) + countLeaf(root->right);
}
int countNonLeaf(struct Node* root) {
    if (root == NULL || (root->left == NULL && root->right == NULL)) return 0;
    return 1 + countNonLeaf(root->left) + countNonLeaf(root->right);
}
int main() {
    struct Node* root = NULL;
    root = insert(root, 'M');
    insert(root, 'D');
    insert(root, 'T');
    insert(root, 'A');
    insert(root, 'G');
    printf("BST In-order Display: ");
    inorder(root);
    printf("\nLeaf nodes: %d\n", countLeaf(root));
    printf("Non-leaf nodes: %d\n", countNonLeaf(root));
    return 0;
}

Slip 20Q.1) Sort an Array using Insertion Sort: Use Slip 3 Q.1 above.   
Q.2) Construct a BST and Display in Ascending Order (OR Infix to Postfix): Use Slip 5 Q.2 (BST In-order) or Slip 7 Q.2 (Infix to Postfix) above.   
Part 2: Data Communication Lab (ELS-242-MNP) — Hamming Code C SimulationsIf your lab also uses Dev-C++ to simulate Slip 5 (7-Bit Hamming Code Generation) and Slip 6 (Hamming Code Error Detection & Correction) from the Electronics slip booklet, you can compile and run this combined C program:   C
#include <stdio.h>
int main() {
    int data[8], rec[8], i, c1, c2, c4, error_pos;
    /* Slip 5: 7-Bit Even Parity Hamming Code Generation for 4-Bit Data */
    printf("Enter 4-bit data word (D7 D6 D5 D3) separated by spaces: ");
    scanf("%d %d %d %d", &data[7], &data[6], &data[5], &data[3]);
    /* Calculate Even Parity Bits at positions 1, 2, 4 */
    data[1] = data[3] ^ data[5] ^ data[7];
    data[2] = data[3] ^ data[6] ^ data[7];
    data[4] = data[5] ^ data[6] ^ data[7];
    printf("Generated 7-bit Hamming Code (D7 D6 D5 P4 D3 P2 P1): ");
    for (i = 7; i >= 1; i--) {
        printf("%d ", data[i]);
    }
    printf("\n\n");
    /* Slip 6: Hamming Code Error Detection and Correction */
    printf("Enter received 7-bit Hamming code (with 1-bit error) separated by spaces:\n");
    for (i = 7; i >= 1; i--) {
        scanf("%d", &rec[i]);
    }
    c1 = rec[1] ^ rec[3] ^ rec[5] ^ rec[7];
    c2 = rec[2] ^ rec[3] ^ rec[6] ^ rec[7];
    c4 = rec[4] ^ rec[5] ^ rec[6] ^ rec[7];
    error_pos = c4 * 4 + c2 * 2 + c1 * 1;
    if (error_pos == 0) {
        printf("No error detected in received code.\n");
    } else {
        printf("Error detected at bit position: %d\n", error_pos);
        rec[error_pos] = !rec[error_pos]; /* Flip corrupted bit */
        printf("Corrected 7-bit Hamming Code: ");
        for (i = 7; i >= 1; i--) {
            printf("%d ", rec[i]);
        }
        printf("\n");
    }
    return 0;
}
