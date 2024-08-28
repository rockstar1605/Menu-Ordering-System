# Menu-Ordering-System
#include <stdio.h>
#include <time.h>
#include <stdlib.h>
#include <string.h>
// Display menu for Burger King
void displayBurgerKingMenu() {
printf("Menu for Burger King:\n");
printf("1. Burger - ₹250\n");
printf("2. Fries - ₹100\n");
printf("3. Chicken Nuggets - ₹200\n");
printf("4. Onion Rings - ₹150\n");
printf("5. Soda - ₹50\n");
}
// Display menu for Domino's
void displayDominosMenu() {
printf("Menu for Domino's:\n");
printf("1. Pepperoni Pizza - ₹500\n");
printf("2. Margherita Pizza - ₹400\n");
printf("3. BBQ Chicken Pizza - ₹600\n");
printf("4. Garlic Bread - ₹200\n");
printf("5. Soft Drink - ₹75\n");
}
// Current date and time
void getCurrentDateTime(char* buffer) {
time_t now = time(0);
strftime(buffer, 80, "%Y-%m-%d %H:%M:%S", localtime(&now));
}
int main() {
const char* restaurants[2] = {"Burger King", "Dominos"};
const char* burgerKingMenu[5] = {"Burger", "Fries", "Chicken Nuggets",
"Onion Rings", "Soda"};
const char* dominosMenu[5] = {"Pepperoni Pizza", "Margherita Pizza", "BBQ
Chicken Pizza", "Garlic Bread", "Soft Drink"};
const float burgerKingPrices[5] = {250.0, 100.0, 200.0, 150.0, 50.0};
const float dominosPrices[5] = {500.0, 400.0, 600.0, 200.0, 75.0};
const int menuSize = 5;
char order[3][30];
int choice;
char restaurantChoice[20];
float totalBill = 0.0;
char dateTime[80];
printf("Welcome to our restaurant!\n");
printf("Please choose a restaurant (Enter 0 for Burger King, 1 for Dominos):
");
scanf("%d", &choice);
if(choice < 0 || choice >= 2) {
printf("Invalid choice!\n");
return 1;
}
strcpy(restaurantChoice, restaurants[choice]);
printf("Great! You've chosen %s.\n", restaurantChoice);
// Display menu based on user's choice
if (strcmp(restaurantChoice, "Burger King") == 0) {
displayBurgerKingMenu();
} else {
displayDominosMenu();
}
// Take orders
printf("Please enter the numbers corresponding to the items you want to
order (up to three items, separated by spaces): ");
for (int i = 0; i < 3; ++i) {
int item;
scanf("%d", &item);
if (item >= 1 && item <= menuSize) {
strcpy(order[i], (strcmp(restaurantChoice, "Burger King") == 0) ?
burgerKingMenu[item - 1] : dominosMenu[item - 1]);
totalBill += (strcmp(restaurantChoice, "Burger King") == 0) ?
burgerKingPrices[item - 1] : dominosPrices[item - 1];
} else {
printf("Invalid item number entered. Ignoring...\n");
}
}
// Display the bill
printf("\n--- Your Bill ---\n");
printf("Restaurant: %s\n", restaurantChoice);
getCurrentDateTime(dateTime);
printf("Date and Time: %s\n", dateTime);
printf("Order Number: %d\n", rand() % 1000 + 1);
printf("Items Ordered:\n");
for (int i = 0; i < 3; ++i) {
if (strlen(order[i]) > 0) {
printf("- %s\n", order[i]);
}
}
printf("Total Bill: ₹%.2f\n", totalBill);
return 0;
}
