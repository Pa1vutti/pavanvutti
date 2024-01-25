# pavanvutti
class Book:
    def _init_(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn

    def display_info(self):
        return f"{self.title} by {self.author} (ISBN: {self.isbn})"


class EBook(Book):
    def _init_(self, title, author, isbn, file_format):
        super()._init_(title, author, isbn)
        self.file_format = file_format

    def display_info(self):
        return f"{super().display_info()} - Format: {self.file_format}"


class Library:
    def _init_(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

    def display_all_books(self):
        return [book.display_info() for book in self.books]

    def search_by_title(self, title):
        return [book.display_info() for book in self.books if title.lower() in book.title.lower()]


# Example usage
try:
    book1 = Book("The Catcher in the Rye", "J.D. Salinger", "978-0-316-76948-0")
    ebook1 = EBook("Python Crash Course", "Eric Matthes", "978-1-59327-603-4", "PDF")

    library = Library()
    library.add_book(book1)
    library.add_book(ebook1)

    print("All Books:")
    print(library.display_all_books())

    search_title = "python"
    print(f"\nBooks containing '{search_title}':")
    print(library.search_by_title(search_title))

except Exception as e:
    print(f"An error occurred: {e}")
