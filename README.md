# chaldal
import request
from bs4 import Beautifulsoup
import pandas as pd
url = "https://chaldal.com/rices"
response = requests.get(url).text
soup = BeautifulSoup(response,"html.parser")
pr= soup.find("div", class_="productPane")
company_name = []
quantity = []
price = []
for r in pr:
    company_name.append(r.find("div", class_="name").get_text())
    quantity.append(r.find("div", class_= "subText").get_text())
    price.append(r.find("div", class_= "price").get_text())
data = pd.DataFrame({"brand" : company_name, "quantity" : quantity,"price" : price})
data
data["price"] = data["price"].str.replace("৳", "").str.replace(",", "").str.strip().astype(int)
print(data)

#for lentil data

url2 = "https://chaldal.com/dal-or-lentil"
response2 = requests.get(url2).text
soup2 = BeautifulSoup(response,"html.parser")
pr2 = soup.find("div", class_="productPane")
company_name2 = []
quantity2 = []
price2 = []
for r2 in pr2:
    company_name2.append(r2.find("div", class_="name").get_text())
    quantity2.append(r2.find("div", class_= "subText").get_text())
    price2.append(r2.find("div", class_= "price").get_text())

data2 = pd.DataFrame({"brand" : company_name, "quantity" : quantity,"price" : price})

data2["price"] = data2["price"].str.replace("৳", "").str.replace(",", "").str.strip().astype(int)
print(data2)

#for salt data

url23 = "https://chaldal.com/search/salt"
response23 = requests.get(url23).text
soup23 = BeautifulSoup(response,"html.parser")
pr23 = soup.find("div", class_="productPane")
company_name23 = []
quantity23 = []
price23 = []
for r23 in pr23:
    company_name23.append(r23.find("div", class_="name").get_text())
    quantity23.append(r23.find("div", class_= "subText").get_text())
    price23.append(r23.find("div", class_= "price").get_text())

data23 = pd.DataFrame({"brand" : company_name, "quantity" : quantity,"price" : price})

data23["price"] = data23["price"].str.replace("৳", "").str.replace(",", "").str.strip().astype(int)
print(data23)





 
