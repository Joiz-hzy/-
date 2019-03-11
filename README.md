# -import java.util.Scanner;

public class _3_00_ConversionOfNumberSystems {
    public static void main(String[] args) {
        System.out.println("Bin - 二    Oct - 八    Dec - 十    Hex - 十六");
        System.out.println("1. Bin to Oct     2. Bin to Dec    3. Bin to Hex");
        System.out.println("4. Oct to Bin     5. Oct to Dec    6. Oct to Hex");
        System.out.println("7. Dec to Bin     8. Dec to Oct    9. Dec to hex");
        System.out.println("10.Hex to Bin     11.Hex to Oct    12.Hex to Dec");
        System.out.println("Enter your choice:");
        Scanner input = new Scanner(System.in);
        int choice = input.nextInt();

        while (choice < 1 || 12 < choice){
            System.out.println("Wrong choice.");
            System.out.println("Please try again:");
            choice = input.nextInt();
        }

        String numberInput;
        if (1 <= choice && choice <= 3){
            System.out.println("Enter your number in Bin:");
            Scanner input1 = new Scanner(System.in);
            String numberInBin = input1.nextLine();
            while (isABin(numberInBin) == false){
                System.out.println("Wrong input.");
                System.out.println("Please try again:");
                numberInBin = input1.next();
            }
            numberInput = numberInBin;

        }
        else if (4 <= choice && choice <= 6){
            System.out.println("Enter your number in Oct:");
            Scanner input1 = new Scanner(System.in);
            String numberInOct = input1.nextLine();
            while (isAOct(numberInOct) == false) {
                System.out.println("Wrong input.");
                System.out.println("Please try again:");
                numberInOct = input1.next();
            }
            numberInput = numberInOct;

        }
        else if (7 <= choice && choice <= 9) {
            System.out.println("Enter your number in Dec:");
            Scanner input1 = new Scanner(System.in);
            String numberInDec = input1.nextLine();
            while (isADec(numberInDec) == false) {
                System.out.println("Wrong input.");
                System.out.println("Please try again:");
                numberInDec = input1.next();
            }
            numberInput = numberInDec;

        }
        else{
            System.out.println("Enter your number in Hex:");
            Scanner input1 = new Scanner(System.in);
            String numberInHex = input1.nextLine();
            while (isAHex(numberInHex) == false) {
                System.out.println("Wrong input.");
                System.out.println("Please try again:");
                numberInHex = input1.next();
            }
            numberInput = numberInHex;

        }

        switch (choice){
            case 1:System.out.println("The number " + numberInput + " in Oct is " + BintoOct(numberInput));break;
            case 2:System.out.println("The number " + numberInput + " in Dec is " + BinToDec(numberInput));break;
            case 3:System.out.println("The number " + numberInput + " in Hex is " + BinToHex(numberInput));break;
            case 4:System.out.println("The number " + numberInput + " in Bin is " + OctToBin(numberInput));break;
            case 5:System.out.println("The number " + numberInput + " in Dec is " + OctToDec(numberInput));break;
            case 6:System.out.println("The number " + numberInput + " in Hex is " + OctToHex(numberInput));break;
            case 7:System.out.println("The number " + numberInput + " in Bin is " + DecToBin(numberInput));break;
            case 8:System.out.println("The number " + numberInput + " in Oct is " + DecToOct(numberInput));break;
            case 9:System.out.println("The number " + numberInput + " in Hex is " + DecToHex(numberInput));break;
            case 10:System.out.println("The number " + numberInput + " in Bin is " + HexToBin(numberInput));break;
            case 11:System.out.println("The number " + numberInput + " in Oct is " + HexToOct(numberInput));break;
            case 12:System.out.println("The number " + numberInput + " in Dec is " + HexToDec(numberInput));break;
        }


    }

    public static boolean isABin(String str){
        for (int i = str.length(); --i >= 0; ) {
            int chr = str.charAt(i);
            if (chr < 48 || 49 < chr)
                return false;
        }
        return true;
    }

    public static boolean isAOct(String str){
        for (int i = str.length(); --i >= 0; ) {
            int chr = str.charAt(i);
            if (chr < 48 || 55 < chr)
                return false;
        }
        return true;
    }

    public static boolean isADec(String str) {
        for (int i = str.length(); --i >= 0; ) {
            int chr = str.charAt(i);
            if (chr < 48 || 57 < chr)
                return false;
        }
        return true;
    }

    public static boolean isAHex(String str){
        for (int i = str.length(); --i >= 0; ) {
            int chr = str.charAt(i);
            if (chr < 48 || 57 < chr && chr < 65 || 70 < chr)
                return false;
        }
        return true;
    }

    public static int BinToDec(String str){
        int dec= 0;
        for (int i =0;i < str.length();i++ ) {
            char binchar = str.charAt(i);
            dec = dec* 2 + binchar - '0';
        }
        return dec;
    }


    public static int OctToDec(String str){
        int dec= 0;
        for (int i =0;i < str.length();i++ ) {
            char octchar = str.charAt(i);
            dec = dec* 8 + octchar - '0';
        }
        return dec;
    }


    public static int HexToDec(String str){
        int dec = 0;
        for (int i = 0;i < str.length(); i++ ){
            char hexchar = str.charAt(i);
            dec = dec * 16 + HexcharToDec(hexchar);
        }
        return dec;
    }
    public static int HexcharToDec(char ch){
        if (ch >= 'A'  && ch <= 'F')
            return 10 + ch - 'A';
        else
            return ch - '0';
    }


    public static String OctToBin(String str){
        String numberInBin = "";
        int numberInDec = OctToDec(str);

        do {
            int OctValue = numberInDec % 2;
            numberInDec = numberInDec / 2;
            numberInBin = OctValue + numberInBin;
        } while (numberInDec != 0);
        return numberInBin;
    }


    public static String DecToBin(String str){
        String numberInBin = "";
        int numberInDec = Integer.parseInt(str);

        do {
            int OctValue = numberInDec % 2;
            numberInDec = numberInDec / 2;
            numberInBin = OctValue + numberInBin;
        } while (numberInDec != 0);
        return numberInBin;
    }


    public static String HexToBin(String str){
        String numberInBin = "";
        int numberInDec = HexToDec(str);

        do {
            int OctValue = numberInDec % 2;
            numberInDec = numberInDec / 2;
            numberInBin = OctValue + numberInBin;
        } while (numberInDec != 0);
        return numberInBin;
    }


    public static String BintoOct(String str){
        String numberInOct = "";
        int numberInDec = BinToDec(str);

        do {
            int OctValue = numberInDec % 8;
            numberInDec = numberInDec / 8;
            numberInOct = OctValue + numberInOct;
        } while (numberInDec != 0);
        return numberInOct;

    }


    public static String DecToOct(String str){
        String numberInOct = "";
        int numberInDec = Integer.parseInt(str);
        do {
            int OctValue = numberInDec % 8;
            numberInDec = numberInDec / 8;
            numberInOct = OctValue + numberInOct;
        } while (numberInDec != 0);
        return numberInOct;

    }


    public static String HexToOct(String str){
        String numberInOct = "";
        int numberInDec = HexToDec(str);

        do {
            int OctValue = numberInDec % 8;
            numberInDec = numberInDec / 8;
            numberInOct = OctValue + numberInOct;
        } while (numberInDec != 0);
        return numberInOct;
    }


    public static String  BinToHex(String str){
        String numberInHex = "";
        int numberInDec = BinToDec(str);
        do {
            int hexValue = numberInDec % 16;
            numberInDec = numberInDec / 16;
            char hexDigit = (0 <= hexValue && hexValue <= 9) ? (char) (hexValue + '0') : (char) (hexValue - 10 + 'A');
            numberInHex = hexDigit + numberInHex;
        } while (numberInDec != 0);
        return numberInHex;
    }


    public static String  OctToHex(String str){
        String numberInHex = "";
        int numberInDec = OctToDec(str);
        do {
            int hexValue = numberInDec % 16;
            numberInDec = numberInDec / 16;
            char hexDigit = (0 <= hexValue && hexValue <= 9) ? (char) (hexValue + '0') : (char) (hexValue - 10 + 'A');
            numberInHex = hexDigit + numberInHex;
        } while (numberInDec != 0);
        return numberInHex;
    }


    public static String DecToHex(String str) {
        String numberInHex = "";
        int numberInDec = Integer.parseInt(str);
        do {
            int hexValue = numberInDec % 16;
            numberInDec = numberInDec / 16;
            char hexDigit = (0 <= hexValue && hexValue <= 9) ? (char) (hexValue + '0') : (char) (hexValue - 10 + 'A');
            numberInHex = hexDigit + numberInHex;
        } while (numberInDec != 0);
        return numberInHex;
    }




}
