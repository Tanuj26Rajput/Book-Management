# Book-Management

#include <iostream>
#include <string>
#include <vector>
using namespace std;

class BookManagement{
public:
    vector<vector<string>> book;
    vector<string> single_book;

    void InsertBook(string book_name, string author_name, int book_id, int price){          //function for inserting book data
        string book_id2 = to_string(book_id);                                   
        string price2 = to_string(price);
        single_book.push_back(book_name);
        single_book.push_back(author_name);
        single_book.push_back(book_id2);
        single_book.push_back(price2);
        book.push_back(single_book);
        cout << "Book added Successfully" << endl << endl;
    }

    void display(){                //function for displaying book data
        if(book.empty()){
            cout << "No books to display" << endl << endl;
            return;
        }
        for(int i = 0; i<book.size(); i++){
            cout << "Book Name: " << book[i][0] << endl;
            cout << "Author Name: " << book[i][1] << endl;
            cout << "Book ID: " << book[i][2] << endl;
            cout << "Book price: "<< book[i][3] << endl;
            cout << "-----------------------------------" << endl << endl;
        }
    }

    void deleteBook(int id){                                //function for deleting book data
        for(int i = 0;i<book.size();i++){       
            if(book[i][2] == to_string(id)){
                book.erase(book.begin()+i);
                cout << "book deleted successfully" << endl << endl;
                return;
            }
        }
        cout << "Book not found" << endl;
    }
};

int main(){
    BookManagement manager;
    while(true){
        cout << "Welcome to the Books Management System" <<endl;               //displaying menu
        cout << "1. Add a book" << endl;
        cout << "2. Display all books" << endl;           
        cout << "3. Delete a book" << endl;
        cout << "4. Exit" << endl;
        int choice;
        cout << "Enter your choice: ";
        cin >> choice;
        switch(choice){
            case 1:{
                cin.ignore();
                string book_name, author_name;                  //fetching data from user
                int Book_id, price;
                cout << "Enter the book name: ";
                getline(cin, book_name);
                cout << "Enter the author name: ";
                getline(cin, author_name);
                cout << "Enter the book id: ";
                cin >> Book_id;
                cout << "Enter the price: ";
                cin >> price;
                manager.InsertBook(book_name, author_name, Book_id, price);
                break;
            }
            case 2: {
                cout << "Displaying all books" << endl;
                manager.display();
                break;
            }
            case 3: {
                int id;
                cout << "Enter ID of the book you want to delete: ";
                cin >> id;
                manager.deleteBook(id);
                break;
            }
            default:
                cout << "Invalid choice" << endl;
        }
    }
    return 0;
}
