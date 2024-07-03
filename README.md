# vending-machine
#include <stdio.h>

// Function to display the menu
void displayMenu()
{
    printf("1. Sandwich - Rs 50\n");
    printf("2. Chips - Rs 20\n");
    printf("3. Chocolate - Rs 30\n");
    printf("4. Soda - Rs 25\n");
	printf("5. Popcorn - Rs 50\n");
	printf("6. French fries - Rs 70\n");
	printf("7. pizza - Rs 100\n");
	printf("8. Burger - Rs 120\n");
	printf("9. Nuts - Rs 60\n");
	printf("10. Energy Drink - Rs 30\n");
    printf("11. Exit\n");
}

// Function to calculate change
void calculateChange(int change)
{
    int denominations[] = {2000, 500, 200, 100, 50, 20, 10, 5, 2, 1};
    int count;
    
    printf("Change to be returned: Rs %d\n", change);
    for(int i = 0; i < 10; i++)
	{
        if(change >= denominations[i])
		{
            count = change / denominations[i];
            change = change % denominations[i];
            printf("%d x Rs %d\n", count, denominations[i]);
        }
    }
}

int main()
{
    int choice, amount, price = 0, change;
	printf("Step right up to our vending delight! Where cravings meet their match and every snack is a bite-sized adventure.\n");
    displayMenu();
    
    while(1)
	{
        printf("Please select an item (1-11): ");
        scanf("%d", &choice);
        
        switch(choice)
		{
            case 1: price = 50;break;
            case 2: price = 20; break;
            case 3: price = 30; break;
            case 4: price = 25; break;
			case 5: price = 50; break;
			case 6: price = 70; break;
			case 7: price = 100; break;
			case 8: price = 120; break;
			case 9: price = 60; break;
			case 10: price = 30; break;
			
            case 11: printf("Until next time, may your snacks be tasty and your cravings satisfied,happy vending:)\n");
			return 0;
            default: printf("Invalid choice! Please try again.\n");
			continue;
        }
        
        printf("You selected item %d. Price: Rs %d\n", choice, price);
        printf("Please enter the amount in Rs: ");
        scanf("%d", &amount);
        
        if(amount < price)
		{
            printf("OOPS! Amount was insufficient ,Please insert at least Rs %d.\n", price);
        } 
		else
		{
            change = amount - price;
            if(change > 0)
			{
                calculateChange(change);
            } else {
                printf("Exact amount received. No change to be returned.\n");
            }
        }
    }
    
    return 0;
}

