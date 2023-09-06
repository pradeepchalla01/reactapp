# reactapp
import java.util.*;
import java.util.stream.Collectors;

public class CompareArraysJava8 {
    public static void main(String[] args) {
        List<Map<String, String>> list1 = new ArrayList<>();
        List<Map<String, String>> list2 = new ArrayList<>();

        // Populate list1 and list2 with your objects (maps with key-value pairs).

        // Using Java 8 streams to perform the operations
        List<Map<String, String>> modifiedList = list1.stream()
                .filter(obj1 -> list2.stream()
                        .anyMatch(obj2 -> obj1.get("countryCode").equals(obj2.get("countryCode"))
                                && !obj1.get("value").equals(obj2.get("value"))))
                .collect(Collectors.toList());

        List<Map<String, String>> newList = list2.stream()
                .filter(obj2 -> list1.stream()
                        .noneMatch(obj1 -> obj1.get("countryCode").equals(obj2.get("countryCode"))))
                .collect(Collectors.toList());

        List<Map<String, String>> expiryList = list1.stream()
                .filter(obj1 -> list2.stream()
                        .noneMatch(obj2 -> obj1.get("countryCode").equals(obj2.get("countryCode"))))
                .collect(Collectors.toList());

        // Now, modifiedList contains objects from list1 with different values in list2,
        // newList contains objects from list2 not in list1,
        // and expiryList contains objects from list1 not in list2.
    }
}
