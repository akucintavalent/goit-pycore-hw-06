Python Programming: Foundations and Best Practices 2.0

# Homework Assignment #6

A Python implementation of a phonebook system that manages contacts and their phone numbers.

## Overview

This project provides a simple yet efficient address book with support for managing contacts, storing phone numbers, and performing operations like adding, editing, and removing phone numbers from contacts.

## Features

- **Contact Management**: Create and manage contacts with names
- **Phone Number Storage**: Add multiple phone numbers to each contact
- **Phone Validation**: Ensures phone numbers are valid 10-digit strings
- **Phone Operations**:
  - Add phone numbers to contacts
  - Edit existing phone numbers
  - Remove phone numbers
  - Find phone numbers within a contact
- **Address Book**: Store and retrieve contacts efficiently using a dictionary-based structure

## Project Structure

```
task_phonebook.py    # Main implementation file
```

## Class Definitions

### `Field`
Base class for contact information fields.

### `Name` (extends `Field`)
Represents a contact's name.

### `Phone` (extends `Field`)
Represents a phone number with validation:
- Must be exactly 10 digits
- Raises `ValueError` if invalid

### `Record`
Represents a contact with:
- `name`: The contact's name (Name object)
- `phones`: List of associated phone numbers (Phone objects)

**Methods:**
- `add_phone(phone)`: Add a phone number to the contact
- `edit_phone(old_phone, new_phone)`: Replace a phone number
- `find_phone(phone)`: Search for a specific phone number
- `remove_phone(phone)`: Delete a phone number
- `__str__()`: Display contact information

### `AddressBook` (extends `UserDict`)
Collection of contacts with:
- `add_record(record)`: Add a new contact
- `find(name)`: Retrieve a contact by name
- `delete(name)`: Remove a contact

## Usage Example

```python
# Create an address book
book = AddressBook()

# Create a contact
contact = Record("John Doe")

# Add phone numbers (must be 10 digits)
contact.add_phone("1234567890")
contact.add_phone("0987654321")

# Add contact to address book
book.add_record(contact)

# Find a contact
found = book.find("John Doe")
print(found)  # Contact name: John Doe, phones: 1234567890; 0987654321

# Edit a phone number
contact.edit_phone("1234567890", "5555555555")

# Remove a phone number
contact.remove_phone("0987654321")
```

## Requirements

- Python 3.6+

## Error Handling

The application includes validation:
- Invalid phone numbers (non-digits or incorrect length) raise `ValueError`
- Attempting to add duplicate phone numbers raises `ValueError`
- Phone edits verify that the old phone number exists
