# Password-generator-
Password generator 
import java.util.Random;

public class PasswordGenerator {

    private static final String LOWERCASE_CHARS = "abcdefghijklmnopqrstuvwxyz";

    private static final String UPPERCASE_CHARS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

    private static final String NUMBERS = "0123456789";

    private static final String SPECIAL_CHARS = "!@#$%^&*()_+-=[]{}\\|;':\",./<>?";

    

    public static void main(String[] args) {

        int length = 12; // default password length

        boolean useUppercase = true;

        boolean useNumbers = true;

        boolean useSpecialChars = true;

        

        // Read command-line arguments (if any) to customize the password options

        if (args.length >= 1) {

            length = Integer.parseInt(args[0]);

        }

        if (args.length >= 2) {

            useUppercase = Boolean.parseBoolean(args[1]);

        }

        if (args.length >= 3) {

            useNumbers = Boolean.parseBoolean(args[2]);

        }

        if (args.length >= 4) {

            useSpecialChars = Boolean.parseBoolean(args[3]);

        }

        

        // Generate the password

        String password = generatePassword(length, useUppercase, useNumbers, useSpecialChars);

        System.out.println("Your password is: " + password);

    }

    

    private static String generatePassword(int length, boolean useUppercase, boolean useNumbers, boolean useSpecialChars) {

        String chars = LOWERCASE_CHARS;

        if (useUppercase) {

            chars += UPPERCASE_CHARS;

        }

        if (useNumbers) {

            chars += NUMBERS;

        }

        if (useSpecialChars) {

            chars += SPECIAL_CHARS;

        }

        

        StringBuilder sb = new StringBuilder();

        Random random = new Random();

        for (int i = 0; i < length; i++) {

            int index = random.nextInt(chars.length());

            char c = chars.charAt(index);

            sb.append(c);

        }

        

        return sb.toString();

    }

}
