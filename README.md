import 'dart:io';

void main() {
  List<String> inventory = ['apple', 'banana', 'carrot', 'dates'];

  while (true) {
    print(' ');
    print('Please select an operation to do:');
    print('[1] Add New Product in the inventory');
    print('[2] Remove a Product from the inventory');
    print('[3] Display the total number of items in the inventory');
    print('[4] Search for an item and display if it is available or not');
    print('[5] Sort the inventory list alphabetically');
    print('[6] Exit');

    stdout.write('You have selected: ');
    String? option = stdin.readLineSync();

    switch (option) {
      case '1':
        stdout.write('Please enter a product you want to add on the list:');
        String? newProduct = stdin.readLineSync();
        if (newProduct != null && newProduct.isNotEmpty) {
          inventory.add(newProduct);
          print('The updated product list are as follows: $inventory');
        }
        break;

      case '2':
        stdout.write('Please enter a product you want to remove on the list:');
        String? removeProduct = stdin.readLineSync();
        if (removeProduct != null && inventory.contains(removeProduct)) {
          inventory.remove(removeProduct);
          print('Updated Inventory after removal: $inventory');
        } else {
          print('$removeProduct not found in the inventory.');
        }
        break;

      case '3':
        print('Total number of items in inventory: ${inventory.length}');
        break;

      case '4':
        stdout.write('Please enter a product you want to search on the list:');
        String? searchProduct = stdin.readLineSync();
        if (searchProduct != null && inventory.contains(searchProduct)) {
          print('$searchProduct is available in the inventory.');
        } else {
          print('$searchProduct is not available in the inventory.');
        }
        break;

      case '5':
        inventory.sort();
        print('Sorted Inventory: $inventory');
        break;

      case '6':
        print('Exiting the program');
        return;

      default:
        print('Invalid choice. Please select a valid option.');
    }
  }
}
