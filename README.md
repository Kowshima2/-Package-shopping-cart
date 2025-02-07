# -Package-shopping-cart
import java.util.*;

class Item {
    String name; double price; int quantity;
    public Item(String name, double price, int quantity) {
        this.name = name; this.price = price; this.quantity = quantity;
    }
    @Override public String toString() {
        return name + " - $" + price + " x " + quantity + " = $" + (price * quantity);
    }
}

class ShoppingCart {
    private final List<Item> cart = new ArrayList<>();
    public void addItem(String name, double price, int quantity) {
        cart.add(new Item(name, price, quantity));
    }
    public void removeItem(String name) {
        cart.removeIf(item -> item.name.equalsIgnoreCase(name));
    }
    public void viewCart() {
        cart.forEach(System.out::println);
    }
    public void checkout() {
        System.out.println("Total: $" + cart.stream().mapToDouble(i -> i.price * i.quantity).sum());
        cart.clear();
    }
}
 public static void main(String[] args)
        Scanner scanner = new Scanner(System.in);
        ShoppingCart cart = new ShoppingCart();
        while (true) {
            System.out.println("1. Add\n2. Remove\n3. View\n4. Checkout\n5. Exit");
            int choice = scanner.nextInt(); scanner.nextLine();
            switch (choice) {
                case 1 : { System.out.print("Name: "); String name = scanner.nextLine();
                            System.out.print("Price: "); double price = scanner.nextDouble();
                            System.out.print("Quantity: "); int qty = scanner.nextInt(); cart.addItem(name, price, qty); }
                case 2 : { System.out.print("Remove item: "); cart.removeItem(scanner.nextLine()); }
                case 3 : cart.viewCart();
                case 4 : cart.checkout();
                case 5 : { scanner.close(); return; }
                default:System.out.println("Invalid choice.");
            }
        }
    }
}
    
    
Output

1. Add
2. Remove
3. View
4. Checkout
5. Exit
