# Java_review
目前統一使用JDK : JavaSE-1.8

JAVA的基本架構
public class 檔名
{
	public static void main(String[] args) //程式從這邊開始
	{	

	}
}

小觀念
左邊=右邊(右邊存入左邊的意思)
i/=1 equal i=i/1  (+-*/%)(加減乘除餘)
number = number+1  等於  number++ (遞增)
餘數:%
換行:\n
char bbb = 's';
String aaa = "hello";
int number1 = 7;
float number2 = 7.5f;
float result = (float)number1/(float)number2;

列印(點的後面有括號->方法，沒括號->物件)
System.out.println("hello"); //System的out物件裡面的println方法

使用者輸入
import java.util.Scanner;
Scanner scanner = new Scanner(System.in); //scanner為物件名稱
float number = scanner.nextFloat();
String word = scanner.nextLine(); 
//.next()有點像單字的意思，nextLine()為一行文字的意思

if else(可搭配 Scanner)
if(string.equals("__"))
且:&&，或||
if(邏輯) {}
else if(邏輯){}
else if(邏輯){}
...
else{}

巢狀if else
if()
{	
	if...
	else...
}
else
{	
	if...
	else...
}

while迴圈(累加，令result=0，i=1)
while(i<=10) //可設定何時變成false，以中斷迴圈
{
result += i; //result = result + i;
i++;
}
System.out.println(result);

while迴圈(Scanner 與 if else配合設計小遊戲)

while迴圈建立九九乘法表(用樹狀圖思考，外圈是根，內圈是葉)
while(j<10) 
{
	for(int i=1; i<10; i++)
	{
		System.out.print(j + "x" + i + "=" + j*i + " ");
	}
	System.out.println();

	j++;
}

給定0到1之間的小數(double)
float number = (float)Math.random();

switch(if else 比較慢，沒有 break 會印出當前 case 之下之輸出)
switch(輸入)
{
	case 輸入1:
		System.out.println("輸出1");
		break;		
	case 輸入2:
		System.out.println("輸出2");
		break;	
	case 輸入3:
		System.out.println("輸出3");
		break;			
}

for 迴圈(x的遞增在前面就先執行了，while通常是在最後才執行，對於continue 與 break 的執行有細節需要注意)
for(x=0; x<10; x++)
{
	System.out.println(x);
}

圓周率
(正方形裡面畫一個圓，中心點座標為(0,0)，正方形邊長=2，半徑=1)
(面積pi*r*r:L*L = pi:4，(pi/4)*4 = pi)
int hit = 0; //半徑內圓面積
int total = 0; //整個正方形
while(true)
{
	float x = (float)Math.random()*2 - 1; 
	float y = (float)Math.random()*2 - 1;

	if(x*x + y*y < 1) //蒐集半徑<1的點
	{
		hit++;
	}

	System.out.println((float)hit/(float)total*4.0f + "[" + total "]");
	total++;
}

break與continue
(break是跳出迴圈(往下跑)，continue是跳出當前跌代過程(往上跑)
while(i<10) //1 2 3 4 停住，但程式仍執行中
{
	if(i==5)
	{
		continue; //break 測試	
}
	System.out.println(i);
	i++;
}
for(int i=0; i<10; i++) //1到9，但沒有5
{
	if(i==5)
	{
		continue; //break 測試
	}
	System.out.println(i);
}

陣列
int[] students = new int[3];
String[] array = new String[10];
students[0]=10;
students[1]=20;
students[2]=30;
int[] students = new int[]{10,20,30}

投擲骰子
int[] DiceCounter = new int[6];
int NUM_ROLLS = 10000;
float average = (float)NUM_ROLLS/6.0f;
for(int i=0; i<NUM_ROLLS; i++)
{
	int number = (int)(Math.random() * 5.9999999);
	DiceCounter[number] = DiceCounter[number]+1;
}
System.out.println(DiceCounter[0] + " " + (float)(((DiceCounter[0]-average)/average)*100.0f) + "%");
System.out.println(DiceCounter[1] + " " + (float)(((DiceCounter[1]-average)/average)*100.0f) + "%");
System.out.println(DiceCounter[2] + " " + (float)(((DiceCounter[2]-average)/average)*100.0f) + "%");
System.out.println(DiceCounter[3] + " " + (float)(((DiceCounter[3]-average)/average)*100.0f) + "%");
System.out.println(DiceCounter[4] + " " + (float)(((DiceCounter[4]-average)/average)*100.0f) + "%");
System.out.println(DiceCounter[5] + " " + (float)(((DiceCounter[5]-average)/average)*100.0f) + "%");
		
三元運算子
判斷式 ？ 若判斷為真執行區塊 ： 若判斷為假執行區塊
String answer  =  number % 2 == 0 ? "even":"odd";

方法或函式
(寫在Body外面，在身體內呼叫方法)
(void 就不會用return，是印出東西沒有回傳東西)
public static int square(int input) //前面的INT是輸出，後面的INT是輸入
{
	return input*input;
}
public static void print(String word) //印出東西，不用回傳東西
{
System.out.println(word);
}

找質數(1.從1到100內找質數 2.當是質數時(if(TTFFTFF...))，印出來))
public class J16
{
	public static void main(String[] args) 
	{	
		int Limit = 100;
		for(int i=2; i<Limit; i++) //找尋1到100裡面的質數
		{
			if(isPrime(i)) //FFTFFTTTFFTTF...
			{
				System.out.print(i + ",");
			}
		}
	}
	
	public static boolean isPrime(int number)
	{
		for(int i=2; i<number; i++)
		{
			if(number%i==0) //什麼情況是非質數
			{
				return false; //碰到return就不會再往下執行了，已回傳了，方法結束了
			}
		}
		return true; //安然度過for迴圈
	}

參考
int[] arrayA = new int{10, 20, 30}; //建立新物件，陣列的等於是連線
int[] arrayB = arrayA; //B連線到物件{10, 20, 30}

arrayB[1] = 5;
System.out.println(arrayA[1]); //5

arrayA是標籤是地址  {10, 20, 30}是物件是房子

基本資料型態的存取
(方法有更動不太會變)
float number = 0.7f; 
int A = 0; //基本型態為自我個體 為獨立變數

(變數為儲存空間)(類型 名稱)(方法有更動到就會變)
String somestring (參考 物件)
int[] array




交換


int[] A = {0};
int[] B = {10};
int[] tmp;
tmp = A;
A = B; //把B的地址給A，A就會去連B的房子
B = tmp;

array1 與 array2 會互換，但動不到 A 與 B exchange(A, B)
public static void exchange(int[] array1, int[] array2)
{
	int[] tmp = array1;
array1 = array2; 
array2 = tmp;
}

使用範圍(主要看同層大括號)
int x = 7; //int 是型態，x是變數
String x = "aaa"; //String是物件，x是參考
不可以宣告兩次；int y = 500; int y = 500;

int x = 7;
if(true) //執行完就會失憶
{
	int y = 5;
}
print(x); //7
print(y); //有誤


someMethod();
System.out.println(a); //印不出來，因為a的使用範圍只有在方法的括弧裡面
			
public static void someMethod()
{
	int a = 100;
}

