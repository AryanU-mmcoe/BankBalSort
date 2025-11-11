#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define TYPE_SAVINGS 'S'
#define TYPE_CURRENT 'C'
#define TYPE_FD 'F'
#define TYPE_OTHER 'O'
#define MAX_CUSTOMERS 10

struct customer {
    char name[50], address[50];
    char type;
    int cus_id;
    long long aadhar, mobile_no, balance;
};

void sort(struct customer bal[], int n) {
    int i, j;
    struct customer temp;
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (bal[j].balance < bal[j+1].balance) {
                temp = bal[j];
                bal[j] = bal[j+1];
                bal[j+1] = temp;
            }
        }
    }
}

void displayCus(struct customer cus[], int n) {
    int i;
    printf("\n--- Customer Details ---\n");
    for (i = 0; i < n; i++) {
        printf("\nACCOUNT DETAILS FOR CUSTOMER ID : %d", cus[i].cus_id);
        printf("\nName: %s", cus[i].name);
        printf("\nAddress: %s", cus[i].address);
        printf("\nAccount Type: %c", cus[i].type);
        printf("\nMobile Number: %lld", cus[i].mobile_no);
        printf("\nAadhar: %lld", cus[i].aadhar);
        printf("\nAccount Balance: %lld", cus[i].balance);
        printf("\n--------------------------------------------------\n");
    }
}

void addCustomers(struct customer cus[], int n_to_add, int current_n) {
    int i, choice;
    for (i = current_n; i < current_n + n_to_add; i++) {
        printf("\n--- Entering Details for Customer %d ---\n", i + 1);

        printf("Enter your name: ");
        scanf("%s", cus[i].name); 

        printf("Enter your address: ");
        scanf("%s", cus[i].address);

        printf("Enter your Customer id: ");
        scanf("%d", &cus[i].cus_id);

        printf("Enter your Account Type:\n(1 - Saving, 2 - Current, 3 - FD, 4 - Other): ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                cus[i].type = TYPE_SAVINGS; 
                break;
            case 2:
                cus[i].type = TYPE_CURRENT;
                break;
            case 3:
                cus[i].type = TYPE_FD;
                break;
            case 4:
                cus[i].type = TYPE_OTHER;
                break;
            default:
                printf("Invalid Input. Setting type to Other.\n");
                cus[i].type = TYPE_OTHER;
                break;
        }
        
        printf("Enter your Mobile Number: ");
        scanf("%lld", &cus[i].mobile_no);

        printf("Enter your Aadhar: ");
        scanf("%lld", &cus[i].aadhar);

        printf("Enter your Account Balance: ");
        scanf("%lld", &cus[i].balance);
    }
}

void searchCus(struct customer cus[], int n) {
    char searchTerm;
    int found = 0, i;

    printf("Enter account type to search (S for Savings, C for Current, F for FD, O for Other): ");
    scanf(" %c", &searchTerm);

    printf("\n--- Search Results for Type: %c ---\n", searchTerm);
    for (i = 0; i < n; i++) {
        if (cus[i].type == searchTerm) {
            printf("\nACCOUNT DETAILS FOR CUSTOMER ID : %d", cus[i].cus_id);
            printf("\nName: %s", cus[i].name);
            printf("\nAddress: %s", cus[i].address);
            printf("\nAccount Type: %c", cus[i].type);
            printf("\nMobile Number: %lld", cus[i].mobile_no);
            printf("\nAadhar: %lld", cus[i].aadhar);
            printf("\nAccount Balance: %lld", cus[i].balance);
            printf("\n--------------------------------------------------\n");
            found = 1;
        }
    }

    if (!found) {
        printf("No customers found with account type '%c'.\n", searchTerm);
    }
}


int main() {
    int mainchoice, n = 0, num_to_add;
    struct customer cus[MAX_CUSTOMERS]; 

    while(1) {
        printf("\n\tMAIN MENU\n");
        printf("1. Add Customers\n");
        printf("2. Display Customer List\n");
        printf("3. Sort Customers (by balance)\n");
        printf("4. Search a customer based on type of account\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        
        if (scanf("%d", &mainchoice) != 1) {
            printf("Invalid input. Please enter a number.\n");
            while (getchar() != '\n'); 
            continue;
        }

        switch (mainchoice) {
            case 1:
                printf("Enter number of customers to add: ");
                scanf("%d", &num_to_add);

                if (n + num_to_add > MAX_CUSTOMERS) {
                    printf("Cannot add that many customers. Maximum total is %d.\n", MAX_CUSTOMERS);
                    num_to_add = MAX_CUSTOMERS - n;
                }
                if (num_to_add > 0) {
                    addCustomers(cus, num_to_add, n);
                    n += num_to_add;
                }
                break;
            case 2:
                if (n > 0) {
                    displayCus(cus, n);
                } else {
                    printf("No customer data available.\n");
                }
                break;
            case 3:
                if (n > 0) {
                    sort(cus, n);
                    printf("Customers sorted.\n");
                } else {
                    printf("No customer data available to sort.\n");
                }
                break;
            case 4:
                if (n > 0) {
                    searchCus(cus, n);
                } else {
                    printf("No customer data available.\n");
                }
                break;
            case 5:
                printf("Exiting program.\n");
                exit(0);
                break;
            default:
                printf("Invalid Input. Please try again.\n");
        }
    }

    return 0;
}
