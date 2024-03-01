import random
accountbalance=0
    # totalshares=0
purchasedshare=0
currentshare=0
soldshare=0
pershareprice_on_purchase=round(random.uniform(15,18),2)
pershareprice_on_selling= round(random.uniform(15,18),2)
# starttrading=False
def starttrading():




    # def clear_screen():
    #     os.system('cls' if os.name == 'nt' else 'clear')


    def checkaccountbalance():
        global accountbalance
        print("Current Account Balance: $", accountbalance)

    def addbalance():
        global accountbalance
        amount=float(input("Enter the amount to be added to your account: "))
        accountbalance+=amount
        print("\nNew Account Balance: $", accountbalance)

    def buy_shares():
        global accountbalance
        global purchasedshare
        global pershareprice_on_purchase
        global currentshare
        if accountbalance>100:
            print("the amount of per share at this time is =",pershareprice_on_purchase)
            shares=int(input("How many shares would you like to purchase? "))
            shareprice=shares*pershareprice_on_purchase
            if  shareprice<accountbalance:
                print("the total amount of shares you want to purchase=",shareprice)
                click=input("Click 1 if you are ready to buy the share :")
                if click=='1':
                    print(f"congratulations you purchased {shares} shares of amount {shareprice}") 
                purchasedshare+=shares
                currentshare+=shares
                accountbalance-=shareprice
            else:
                print(f"Your account balance is insufficient! first add balance to buy {shares} shares")
        else:
            print("Insuffieient balance! .")
            print("First add balance and then retry!")
        # clear_screen()
        # main()

    def sell_shares():
        global purchasedshare
        global accountbalance
        global soldshare
        global pershareprice_on_selling
        global currentshare
        if  purchasedshare>0:
            print("the amount of per share at this time is =",pershareprice_on_selling)

            share=int(input("Enter the number of shares you want to sell:"))
            if  share<=purchasedshare:
                click=input("click 1 to conferm this Transection:")
                if click=='1':
                    print("the transection is completed")
                    soldshare+=share
                    currentshare-=share    
                    accountbalance+=purchasedshare*pershareprice_on_selling 
                else:
                    print("Transection Cancelled") 
            else:
                print("the number is more than the share purchased") 
        else:
            print("No shares to sell!")
        # clear_screen()
        # main()

    def profile():
        print("\n\n\n")
        print("**************Your Profile***************")
        print("Total amount is your Trading account =",accountbalance)
        print("Total share Availabe=",currentshare)
        print("Total purchased share=",purchasedshare)

        print("Total number of share sold=",soldshare)
        amount=(soldshare*pershareprice_on_purchase)-(soldshare*pershareprice_on_selling)
        if amount<0:
            print("Loss in your trading account =",amount)
        elif amount==0:
            print("your  trading account is balanced")
        else:
            print("your trading account  has made a profit =" ,amount)

    def base():
        while True:


            option = input("Enter your option: ")

            if option == '1':
                checkaccountbalance()
            elif option == '2':
                addbalance()
                # Placeholder for adding balance functionality
            elif option == '3':
                buy_shares()
                # Placeholder for buying shares functionality
            elif option == '4':
                sell_shares()
                # Placeholder for selling shares functionality
            elif option=='5':
                profile()
            elif option == '6':
                print("Exiting program...")
                break
            else:
                print("Invalid option. Please select a valid option.")


    # def main():
    print("Welcome to the trading program")
    print("If you are interested in trading, select an option:")
    print("1. Check account balance")
    print("2. Add balance")
    print("3. Buy shares")
    print("4. Sell shares")
    print("5. View Profile")
    print("6. Exit")
    base()






def create_account():
    global customerid
    print("\n\nCreating an account...")
    name = input("Enter your full name: ")  
     # Generate a unique ID for each user using randint() function from random module 

    username = input("Choose a user name : ")     # Username should be unique, so we
    # need to check if it already exists in our database (list)
    while True:                               # If not, ask again until a valid one is entered
        password = input("Set a password: ")
        confirm_password = input("Confirm Password: ")
        if password == confirm_password:
            break
        else:
            print("Passwords do not match.")
    # Add new user details to the 'database' - list of dictionaries
    accounts.append({'Name': name,'Username':username,'Password':password,'customerid':customerid})
    print(f"\nAccount created for {name}! And customerid is  {customerid}")
    customerid+=1




def login_account():
    found = False
    while not found:
        username = input("Enter your username: ")
        password = input("Enter your password: ")

        for acc in accounts:
            if username == acc['Username'] and password == acc['Password']:
                found = True
                print(f"Logged in as {acc['Name']}")
                # starttrading=True
                # if starttrading:
                starttrading()
        else:
            print("Invalid credentials.\nPlease try again.")





print("Welcome       Welcome       Welcome")
print("      ABC Trading Application      ")
print("---------------------------------------")
# Function to display the menu options for users
print("1.Create Accout")
print("2.Login Account  ")
print("3.Exit           ")
accounts=[]
customerid=2500


while True: 
    option = int(input("\nSelect an Option:\n"))
    if option == 1:
        create_account()
    elif option == 2:
        login_account()
    elif option == 3:
        print("\nExiting Program..\n")
        break
    else:
        print("\nInvalid Option!\nPlease enter a valid number from the menu options.\n")









