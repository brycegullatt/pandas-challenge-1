# pandas-challenge-1
Module 4 Challenge

# Code attempts

# Did not know how to solve:
# Create a summary DataFrame showing the totals for the for the top 5 clients with the following information:
# total units purchased, total shipping price, total revenue, and total profit.

#top_client_summary_df = df[["client_id","qty","shipping_price","line_price","line_cost","line_profit"]].copy()
#top_client_summary_df.head()
#for i in top_client_list:
    #top_client_qty = round((df[df["client_id"] == i]["qty"].sum()),2).tolist()
 
#top_client_summary_df = pd.DataFrame(
    #{"client_id":top_client_list,
    # "qty":top_client_qty
#    }
#)
#top_client_summary_df

# (Credit to Lindelwe)
# Create a summary DataFrame showing the totals for the for the top 5 clients with the following information:
# total units purchased, total shipping price, total revenue, and total profit. 
def client_totals(id, column):
    client_df = df.loc[df["client_id"] == id, column]
    return round(client_df.sum(), 2)

client_dict = {"client_id":top_client_list}

summary_columns = ["qty","shipping_price","line_price","line_cost","line_profit"]

for column in summary_columns:
    totals = []
    for client_id in top_client_list:
        totals.append(client_totals(client_id, column))
    client_dict[column] = totals

client_summary_df = pd.DataFrame(client_dict)
client_summary_df