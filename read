 
import java.util.Random; 
import java.util.Scanner; 
 
public class SnakeGame{ 
    static final int COLS = 25; 
    static final int ROWS = 25; 
    static final int FOODS = 30; 
    static char[] board = new char[COLS * ROWS]; 
    static boolean isGameOver = false; 
 
    static class SnakePart { 
        int x, y; 
    } 
 
    static class Snake { 
        int length; 
        SnakePart[] part = new SnakePart[SNAKE_MAX_LEN]; 
        Snake() { 
            for (int i = 0; i < SNAKE_MAX_LEN; i++) { 
                part[i] = new SnakePart(); 
            } 
        } 
    } 
 
    static class Food { 
        int x, y; 
        boolean consumed; 
    } 
 
    static final int SNAKE_MAX_LEN = 256; 
    static Snake snake = new Snake(); 
    static Food[] food = new Food[FOODS]; 
    static Random random = new Random(); 
 
    static void fillBoard() { 
        for (int x = 0; x < ROWS; x++) { 
            for (int y = 0; y < COLS; y++) { 
                if (x == 0 || y == 0 || x == ROWS - 1 || y == COLS - 1) { 
                    board[x * COLS + y] = '#'; 
                } else { 
                    board[x * COLS + y] = ' '; 
                } 
            } 
} 
    } 
 
    static void printBoard() { 
        for (int x = 0; x < ROWS; x++) { 
            for (int y = 0; y < COLS; y++) { 
                System.out.print(board[x * COLS + y]); 
            } 
            System.out.println(); 
        } 
    } 
 
    static void drawSnake() { 
        for (int i = 1; i < snake.length; i++) { 
            board[snake.part[i].y * COLS + snake.part[i].x] = '*'; 
        } 
        board[snake.part[0].y * COLS + snake.part[0].x] = '@'; 
    } 
 
    static void moveSnake(int deltaX, int deltaY) { 
        for (int i = snake.length - 1; i > 0; i--) { 
            snake.part[i].x = snake.part[i - 1].x; 
            snake.part[i].y = snake.part[i - 1].y; 
        } 
        snake.part[0].x += deltaX; 
        snake.part[0].y += deltaY; 
    } 
 
    static void drawFood() { 
        for (int i = 0; i < FOODS; i++) { 
            if (!food[i].consumed) { 
                board[food[i].y * COLS + food[i].x] = '+'; 
            } 
        } 
    } 
 
    static void setupFood() { 
        for (int i = 0; i < FOODS; i++) { 
            food[i] = new Food(); 
            food[i].x = 1 + random.nextInt(COLS - 2); 
            food[i].y = 1 + random.nextInt(ROWS - 2); 
            food[i].consumed = false; 
        } 
    } 
 
    static void setupSnake() { 
        snake.length = 1; 
        snake.part[0].x = 1 + random.nextInt(COLS - 2); 
 snake.part[0].y = 1 + random.nextInt(ROWS - 2); 
    } 
 
    static void gameRules() { 
        for (int i = 0; i < FOODS; i++) { 
            if (!food[i].consumed && food[i].x == snake.part[0].x && food[i].y == snake.part[0].y) { 
                food[i].consumed = true; 
                snake.length++; 
            } 
        } 
        if (snake.part[0].x == 0 || snake.part[0].x == COLS - 1 ||  
            snake.part[0].y == 0 || snake.part[0].y == ROWS - 1) { 
            isGameOver = true; 
        } 
        for (int i = 1; i < snake.length; i++) { 
            if (snake.part[0].x == snake.part[i].x && snake.part[0].y == snake.part[i].y) { 
                isGameOver = true; 
            } 
        } 
    } 
 
    static void clearScreen() { 
       
        System.out.print("\033[H\033[2J"); 
        System.out.flush(); 
    } 
 
    public static void main(String[] args) { 
        Scanner scanner = new Scanner(System.in); 
        setupSnake(); 
        setupFood(); 
 
        while (!isGameOver) { 
            fillBoard(); 
            drawFood(); 
            drawSnake(); 
            gameRules(); 
            clearScreen(); 
            System.out.println("Snake Game, Score: " + ((snake.length - 1) * 100)); 
            printBoard(); 
            if (!isGameOver) { 
                System.out.println("Move (w/a/s/d): "); 
                String input = scanner.nextLine(); 
                switch (input) { 
                    case "w": moveSnake(0, -1); break; 
                    case "s": moveSnake(0, 1); break; 
                    case "a": moveSnake(-1, 0); break; 
                    case "d": moveSnake(1, 0); break;  } 
            } 
        } 
 
        System.out.println("Game Over, Final score: " + ((snake.length - 1) * 100)); 
      
        System.out.println("Press Enter to exit."); 
        scanner.nextLine(); 
        scanner.close(); 
    }
}
