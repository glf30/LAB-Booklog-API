# LAB-Booklog-API

## Objective

Build a backend-only RESTful API using MongoDB and Express that models a book tracking system with authors. This project must demonstrate your ability to:

- Design referenced data relationships
- Structure a modular Express/Mongoose app
- Implement full REST CRUD with real-world logic
- Handle filtering, sorting, and custom route behavior

---

## Entities

### Author
- `name` (String, required)
- `birthYear` (Number, optional)

### Book
- `title` (String, required)
- `author` (ObjectId reference to Author, required)
- `genre` (String, optional)
- `releaseDate` (Date, required)
- `favorite` (Boolean, default: false)
- `notes` (String, optional)

---

## Functionality

### Book Routes – `/api/books`

| Method | Path | Description |
|--------|------|-------------|
| `GET` | `/` | Return all books |
| `GET` | `/:id` | Return a single book with author info |
| `POST` | `/` | Create a new book (must reference a valid author) |
| `PUT` | `/:id` | Update an existing book |
| `DELETE` | `/:id` | Delete a book <br>**Only if not marked `favorite`** |

#### Book Index (`GET /api/books`) must support:
- Sorting by `dateFinished` (descending by default)
- Sorting by **author name** using query param `?sort=author`
- Filtering by:
  - `author` ID: `?author=<authorId>`
  - `genre`: `?genre=fiction`

---

### Author Routes – `/api/authors`

| Method | Path | Description |
|--------|------|-------------|
| `GET` | `/` | Return all authors |
| `GET` | `/:id` | Return a single author **including all their books** |
| `POST` | `/` | Create a new author |
| `PUT` | `/:id` | Update author info |
| `DELETE` | `/:id` | Delete an author <br>**Only if they have no books** |

---

## Requirements

- Use MongoDB with Mongoose models for `Book` and `Author`
- Utilize Models, Controllers, and Routers to organize your codebase
- Use `.populate()` to link books with their authors
- Use query parameters to support filtering and sorting
- Prevent deletion of:
  - Books marked as `favorite: true`
  - Authors who have any associated books

---

## Optional Stretch

If you finish the required functionality, consider one of these:
- Add pagination to `GET /api/books` using `?page=` and `?limit=`
- Add a `PATCH /api/books/:id/favorite` route to toggle a book’s favorite status

---
