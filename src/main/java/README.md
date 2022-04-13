public class JvmComprehension { // C помощью klassloader подгрузились JvmComprehension.class, String.class, Integer.class
Object.class в metaspace

    public static void main(String[] args) { // создался новый фрейм main() в стеке
        int i = 1;                      // 1 в фрейме main() создалась переменая int с именем i cо значением 1
        Object o = new Object();        // 2 в куче создался объект типа Object, в фрейме main() создается ссылка "о" на этот объект
        Integer ii = 2;                 // 3 в куче создался объетк Integer = 2, в фрейме main() создается ссылка "ii" на этот объект
        printAll(o, i, ii);             // 4 в стеке создается новый фрейм printAll(), в котором создаются ссылки на o,i,ii
        System.out.println("finished"); // 7 в стеке создался новый фрейм println(). в куче создался объект типа String = "finished"
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 в куче создался объект Integer с значением 700, в фрейме println() создается ссылка uselessVar на этот объект
        System.out.println(o.toString() + i + ii);  // 6 в стеке создается фрейм toString(), потом println()
    }
}