book_names = []
book_prices = []
num_books = int(input("Enter the number of books in library: "))
 
# Get the name and price of each book from the user
for i in range(num_books):
    name = input("Enter the name of book {}: ".format(i+1))
    price = int(input("Enter the price of book {}: ".format(i+1)))
    book_names.append(name)
    book_prices.append(price)
 
# Print the name and price of all books
print("Name and price of all books:")
for i in range(num_books):
    print("{}: {}".format(book_names[i], book_prices[i]))
 
# Delete duplicate entries
unique_books = []
unique_prices = []
for i in range(num_books):
    if book_names[i] not in unique_books:
        unique_books.append(book_names[i])
        unique_prices.append(book_prices[i])
print("\nName and price of unique books:")
for i in range(len(unique_books)):
    print("{}: {}".format(unique_books[i], unique_prices[i]))
 
# Display books in ascending order based on cost
for i in range(len(unique_prices)):
    for j in range(i + 1, len(unique_prices)):
        if unique_prices[i] > unique_prices[j]:
            unique_prices[i], unique_prices[j] = unique_prices[j], unique_prices[i]
            unique_books[i], unique_books[j] = unique_books[j], unique_books[i]
print("\nName and price of books in ascending order:")
for i in range(len(unique_books)):
    print("{}: {}".format(unique_books[i], unique_prices[i]))
 
# Count number of books with cost more than 500
def count_expen_book(prices):
    count = 0
    for price in prices:
        if price > 500:
            count += 1
    return count
print("\nCount of books having cost more than 500:", count_expen_book(unique_prices))
 
# Copy books in a new list which has cost less than 500
cheap_books = []
cheap_prices = []
for i in range(len(unique_prices)):
    if unique_prices[i] < 500:
        cheap_books.append(unique_books[i])
        cheap_prices.append(unique_prices[i])
