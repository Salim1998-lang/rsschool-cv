## Salim Murtazaaliev
* **E-mail:** <vsalim1998@gmail.com>
* **Telephone number:** +7988 896 81 05
* **Github:** <https://github.com/Salim1998-lang>
* **LinkedIn:** [my page](https://www.linkedin.com/in/%D1%81%D0%B0%D0%BB%D0%B8%D0%BC-%D0%BC%D1%83%D1%80%D1%82%D0%B0%D0%B7%D0%B0%D0%B0%D0%BB%D0%B8%D0%B5%D0%B2-64b4761ab/)


### Summary

> I like to write code and solving complex problems. My current dream is to get a job as a junior android developer. Now I work as a teacher 
> at the IT-cube programming school, where I teach children Java and Kotlin. I wanna to learn Android SDK well. I hope RS-school will help me.

### Technical skills

> Programming languages: Java, Kotlin.
> Frameworks and libraries: Android SDK, Room, Retrofit.
> Tools: IntelIJ Idea, Android Studio.
> Other skills: sociability, power supply design (current work)

### Code example:

public class Main {
    //Объявление глобальных данных
    public static int el1 = 0, el2 = 0, res = 0;
    public static String[] romans = {"I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X", "XI"};
    public static String[] arab = {"1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11"};

    private final static TreeMap<Integer, String> map = new TreeMap<Integer, String>();
    static {
        map.put(100, "C");
        map.put(90, "XC");
        map.put(50, "L");
        map.put(40, "XL");
        map.put(10, "X");
        map.put(9,  "IX");
        map.put(5,  "V");
        map.put(4,  "IV");
        map.put(1,  "I");
    }


    //Функция для вывода ответа
    public static String getValuetoRoman(int number) {
        int l = map.floorKey(number);
        if ( number == l ) {
            return map.get(number);
        }
        return map.get(l) + getValuetoRoman(number-l);
    }


    //Вычисление для арабских символов
    public static int arabNumberCalculate(String number1, String operation, String number2) {
        for (int i = 0; i < arab.length; i++){
            if(number1.equals(arab[i])) {
                el1 = i + 1;
            }
            else if(number2.equals(arab[i])) {
                el2 = i + 1;
            }else if(number1.equals(number2)){
                el2 = el1;
            }
        }
        return valueOperation(el1, operation, el2);
    }


    //Вычисление значений для римских символов
    public static String romanCalculate(String number1, String operation, String number2) {
        for (int i = 0; i < romans.length; i++){
            if(number1.equals(romans[i])) {
                el1 = i + 1;
            }
            else if(number2.equals(romans[i])) {
                el2 = i + 1;
            }else if(number1.equals(number2)){
                el2 = el1;
            }
        }
        return getValuetoRoman(valueOperation(el1, operation, el2));
    }

    public static int valueOperation(int el1, String operation, int el2){
        switch (operation){
            case "+":
                res = el1 + el2;
                break;
            case "-":
                res = el1 - el2;
                break;
            case "*":
                res = el1 * el2;
                break;
            case "/":
                res = el1 / el2;
                break;
            default:
                System.out.println("Это простой калькулятор! Доступно: \n\t сложение; \n\t вычитание; \n\t умножение; \n\t деление; \n");
                break;
        }
        return res;
    }


    //Главная функция main()
    public static void main(String[] args)  {
        Scanner str = new Scanner(System.in);
        String number1 = str.next();
        String operation = str.next();
        String number2 = str.next();

        if(Arrays.asList(romans).contains(number1) && Arrays.asList(romans).contains(number2)) {
            System.out.println(romanCalculate(number1, operation, number2));
        }
        else if(Arrays.asList(arab).contains(number1) && Arrays.asList(arab).contains(number2)){
            System.out.println(arabNumberCalculate(number1,operation,number2));
        }else
            System.out.println(" Ошибка!!! Не стоит совмещать арабские и римские числа!");
    }
}
