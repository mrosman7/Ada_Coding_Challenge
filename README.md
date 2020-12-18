# Ada_Coding_Challenge

#!/bin/python3

#
# Complete the 'subscription_summary' function below.
#

def subscription_summary(months_subscribed, ad_free_months, video_on_demand_purchases):
    """
    Parameters:
      months_subscribed: How many months each account purchased.
      ad_free_months: How many months each account paid for ad free viewing.
      video_on_demand_purchases: How many Videos on Demand each account purchased.
    """
    print("Welcome to the Ada+ Account Dashboard")
    print()

    # variables     
    one_month_cost = 7.00                 # price for one month subscription
    three_month_bundle_cost = 18.00       # price for three month bundle. Assuming if 4 months one will be charges at reugular price 
    monthly_ad_free_cost = 2.00           # additional price per month for Ad-free watching
    video_on_demand_cost = 27.99          # price for one Video on Demand purchase
    total_from_all_accounts = 0           # variable to show the total all accounts have earned 
    premium_watching_total = 0            # variable to show the total all accounts have earned for premium watching
    account_totals_list = []              # list holds values for the total revenue of each account
    accounts_list = []                    # list to hold account informaiton in the form of dictionaries (see for loop below)         

    # input from user is made into a new dictionary which is appended to the accounts_lists list above
    for i in range(0,len(months_subscribed)):   # for every index in months_subscribed list create a new dictionary
        dictionary = {
            "months_subscribed" : months_subscribed[i],
            "ad_free_months" : ad_free_months[i],
            "video_on_demand_purchases" : video_on_demand_purchases[i],
            }
        accounts_list.append(dictionary)          # append each new dictionary to the accounts_list list 
                

    # finds and displays the totals for each service for each account in the accounts_list and displays totals in print statemnts
    for i in range(0,len(accounts_list)):
        dictionary = accounts_list[i]                                                                   # dictionary here is assigned to each index in account_list 
        monthly_sub_total = ((dictionary['months_subscribed'] % 3) * one_month_cost) + ((dictionary['months_subscribed'] // 3) * three_month_bundle_cost)
        monthly_ad_free_total = dictionary['ad_free_months'] * monthly_ad_free_cost
        video_on_demand_total = dictionary['video_on_demand_purchases'] * video_on_demand_cost 
        account_total = monthly_sub_total + monthly_ad_free_total + video_on_demand_total                # account_total is not needed but is better for code organization 
        account_totals_list.append(account_total)                                                        # this appends the account_total list up above 
        total_from_all_accounts += account_total 
        premium_watching_total += monthly_ad_free_total + video_on_demand_total
        print(f"Account {i + 1} made ${account_total:0.2f} total")                                       # formatting {:0.2f} to display numbers to two decimals 
        print(f">>> ${monthly_sub_total:0.2f} from monthly subscription fees")
        print(f">>> ${monthly_ad_free_total:0.2f} from Ad-free upgrades")
        print(f">>> ${video_on_demand_total:0.2f} from Video on Demand purchases")
        print()                                                                                         

    # displays revenue earned by all accounts combines
    print(f"Combined all accounts made ${total_from_all_accounts:0.2f} total")
    #displays total premium content revenue earned by all accounts 
    print(f"Premium content (Ad-free watching and Video on Demand) made ${premium_watching_total:0.2f} total")
    print()

    # list and for loop find and display the account that earned the highest revenue
    largest_account_total = account_totals_list[0]
    largest_total_indiceis = []


    for i in account_totals_list:
        if i > largest_account_total:
            largest_account_total = i

    for i in range(0,len(account_totals_list)):
            if account_totals_list[i] == largest_account_total:
                    largest_total_indiceis.append(i + 1)

    #for i in range(0,len(account_totals_list)):
    #    if account_totals_list[i] == largest_account_total:
    #        largest_total_indiceis.append(i + 1)
    #    if account_totals_list[i] > largest_account_total:
    #        largest_total_indiceis = []
    #        largest_total_indiceis.append(i + 1)

    print(f"${largest_account_total:0.2f} was the most earned by any single account")
    # displays the index of the largest number in the list above (largest_total_account) 
    print("The accounts that earned the most were:", *largest_total_indiceis, sep=" #")   # +1 added because the Account# will be one larger than the index
    print()                                                                                          # example: Account 1 is located at [0]


months_subscribed = [5, 5, 3]
ad_free_months = [4, 4, 1]
video_on_demand_purchases = [1, 1, 0]

subscription_summary(months_subscribed, ad_free_months, video_on_demand_purchases)
    

