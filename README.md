# Perpus_Association_Nandasari
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
        self.is_available = True

    def __str__(self):
        return f"{self.title} by {self.author}"

class LibraryMember:
    def __init__(self, name):
        self.name = name
        self.borrowed_books = []

    def borrow_book(self, book):
        if book.is_available:
            book.is_available = False
            self.borrowed_books.append(book)
            print(f"{self.name} telah meminjam buku: {book}")
        else:
            print(f"Maaf, buku {book} tidak tersedia.")

    def return_book(self, book):
        if book in self.borrowed_books:
            self.borrowed_books.remove(book)
            book.is_available = True
            print(f"{self.name} telah mengembalikan buku: {book}")
        else:
            print(f"Buku {book} tidak dipinjam {self.name}.")

    def display_borrowed_books(self):
        if self.borrowed_books:
            print(f"Buku yang dipinjam {self.name}:")
            for book in self.borrowed_books:
                print(book)
        else:
            print(f"{self.name} tidak meminjam buku apapun.")


# Contoh penggunaan program
book1 = Book("Python Programming", "John Smith")
book2 = Book("Java Basics", "Jane Doe")
book3 = Book("C++ Fundamentals", "Alice Johnson")

member1 = LibraryMember("John")
member2 = LibraryMember("Alice")

member1.borrow_book(book1)
member1.borrow_book(book2)
member1.borrow_book(book3)

member2.borrow_book(book2)
member2.borrow_book(book3)

member1.return_book(book2)
member2.return_book(book3)

member1.display_borrowed_books()
member2.display_borrowed_books()

