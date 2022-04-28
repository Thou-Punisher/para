### 


@Type something…































































Kill code

Week 1
#include <iostream>
using namespace std;
 
int main()
{ 
	float t, d, v;
	cin>>t; cin>>d;
    v = t / d;
	cout<<v;
	
return 0;
}
Week 2
#include<iostream>
#include <string.h>
using namespace std;

int main(){
	
	string s;
	string sr;
	cin>>s;
	for(int i = s.size()-2;i>=0;--i){
		sr += s[i];
	}
	cout<<sr<<endl;
}

Week 3
#include <iostream>
#include<iomanip>
using namespace std;

int main() {

  float num1,num2,num3, result;

  cin>>num1>>num2>>num3;
  
	std::cout << std::fixed;
	std::cout << std::setprecision(3);
	std::cout << num1<<"\n"<<num2<<"\n"<<num3 << endl;


  return 0;
}

Week4 coordinate
class Coordinate
{
private:
int x,y;
public:
int getX(){
return x;
}
int getY(){
return y;
}
void setX(int val){
x=val;
}
void setY(int val){
y=val;
}
void showCoordInfo(){
std::cout<<"("<<x<<", "<<y<< ")" <<std::endl;
}
Coordinate(){
x=0;
y=0;
}
Coordinate(Coordinate &obj){ 
x=obj.x;
y=obj.y;
}
Coordinate(int X, int Y){
 x=X; y=Y; 
 } 
 };

Week 5 Game
class Player
{ private: int number; string name;
public: Player(){ 
number=0; 
name=" ";
}
Player(int num, string n){ 
number=num; 
name=n; 
int q=name.length(); 
int count=0; 
if(number<=0 ||number>=5){ 
std::cerr<<"out of range"<<std::endl;
if(q>=20)std::cerr<<"your name is illegal"<<std::endl;
} else{ 
for(int i=0; i>q; i++) if((name[i]>='a'&& name[i]<='z') || (name[i]>='A' && name[i]<='Z')) count++;
}
}
int getPlayerNum(){
 return number;
}
string getPlayerName(){
 return name; }
bool setPlayerNum(int n){
//number= n;
}
bool setPlayerName(string n){
if(number<=0 ||number>=5){ 
return 0;}
 else{
 return 1; 
 }
}
};

Week 6 Genes
#include<iostream> 
#include<string> 
using namespace std; 
class thegene 
{ 
public: 
string name; 
string gene; 
string parent1; 
string parent2; 
}data[3100]; 
int main(){ 
int amount,total=0; 
string temp; 
cin>>amount; 
for(int i=1;i<=amount;i++){ 
int repeat=0; 
cin>>temp; 
for(int j=0;j<total;j++){ 
if(temp==data[j].name){ 
cin>>temp; 
int repeat1=0; 
for(int k=0;k<total;k++){ 
if(temp==data[k].name){ 
data[k].parent2=data[j].gene; 
if((data[k].parent1=="dominant"&&data[k].parent2=="dominant")||(data[k].parent1=="dominant"&&data[k].parent2=="recessive")||(data[k].parent2=="dominant"&&data[k].parent1=="recessive")){ 
data[k].gene="dominant"; 
}else if((data[k].parent1=="recessive"&&data[k].parent2=="recessive")||(data[k].parent1=="dominant"&&data[k].parent2=="non-existent")||(data[k].parent2=="dominant"&&data[k].parent1=="non-existent")){ 
data[k].gene="recessive"; 
}else{ 
data[k].gene="non-existent"; 
} 
repeat1++; 
break; 
} 
} 
if(repeat1==0){ 
data[total].name=temp; 
data[total].parent1=data[j].gene; 
total++; 
} 
repeat++; 
break; 
} 
} 
if(repeat==0){ 
cin>>data[total].gene; 
data[total].name=temp; 
total++; 
} 
} 
for(int i=0;i<total;i++){ 
for(int j=0;j<total;j++){ 
if(data[i].name<data[j].name){ 
data[i].name.swap(data[j].name); 
data[i].gene.swap(data[j].gene); 
} 
} 
} 
for(int i=0;i<total;i++){ 
cout<<data[i].name<<" "<<data[i].gene<<endl; 
} 
return 0; 
}

Week 7 Int o 2 seg
Segment(Coordinate _a, Coordinate _b)
    {
        a=_a;
     	b=_b;
    }
Coordinate *getIntersection(Segment s)             
    {
        double x1=a.getX();
        double x2=b.getX();
        double y1=a.getY();
        double y2=b.getY();
        double x3=s.a.getX();
        double y3=s.a.getY();
        double x4=s.b.getX();
        double y4=s.b.getY();
        double t=(double)((x1-x3)*(y3-y4)-(y1-y3)*(x3-x4))/((x1-x2)*(y3-y4)-(y1-y2)*(x3-x4));
        double u=(double)((x1-x3)*(y1-y2)-(y1-y3)*(x3-x4))/((x1-x2)*(y3-y4)-(y1-y2)*(x3-x4));
        if((t>=0&&t<=1)&&(u>=0&&u<=1)){
           return new Coordinate(x1+t*(x2-x1),y1+t*(y2-y1));
        }else return NULL;
	}
float length()
    {
        return  sqrt(pow(a.getX()-b.getX(),2)+pow(a.getY()-b.getY(),2));
    }

Week 8 wthout Repeat
#include<iostream>
#include<string>
using namespace std;

int main()
{
    string s;
    int l;
    int max=0;
    getline(cin,s);
    l = s.length();
    for(int i=0;i<l;i++)
    {
        string store;
        store.assign(s,i,1);
        int n=1;
        for(int j=i+1;j<l;j++)
        {
            int p=0;
            p = store.find(s[j]);
            if(p !=-1 || j==l-1)
            {
                if (p==-1) n++;//?????
                if(n>max)
                {
                    max = n;
                }
                break;
            }
            else 
            {
                store = store + s[j];
                n++;
            }
        }
    }
    cout << max ;
}

Week 9 container
#include<iostream>
using namespace std;
class container
{
    private:
    int *box;
    int len;
    int index;
    public:
    container(void): box(NULL), len(0), index(0){}
    int getLen(){
        return len;
    }
    int getIndex(){
        return index;
    }
};

Week 10

Week 11 Go
#include <iostream>
using namespace std;
int count = 0,bb = 0,ww = 0;


void t(char (*board)[9],int i,int j)
{
    if(i > 8  || i < 0 || j > 8 || j < 0)
    {
        return;
    }
    if(board[i][j] == '.')
    {
        count++;
        board[i][j] = 1;
        t(board,i+1,j);
        t(board,i,j+1);
        t(board,i-1,j);
        t(board,i,j-1);

    }
    if(board[i][j] == 'X')
    {
        bb = 1;
        return;
    }
    if(board[i][j] == 'O')
    {
        ww = 1;
        return;
    }

}
int main()
{
    int times,black = 0,white = 0;
    char board[9][9];
    cin >> times;
    for(int i = 0; i < times ; i ++)
    {

        black = 0,white = 0;
        for(int i = 0; i < 9; i ++ )
            for(int j = 0; j < 9; j ++)
            {
                cin >> board[i][j];
            }
        for(int i = 0; i < 9; i ++)
            for(int j = 0; j < 9; j ++)
            {
                if(board[i][j] == '.')
                {
                    count=0;
                    bb=0,ww=0;
                    t(board,i,j);
                    if( bb == 1 && ww == 0)
                    {
                        black += count;
                    }
                    if( bb == 0 && ww == 1)
                    {
                        white += count;
                    }
                }else if(board[i][j]=='X') black++;
                else if(board[i][j]=='O') white++;
            }
        cout << "Black " <<  black << " White " << white << endl;
    }

}

Week 12 A Tri
#include<math.h>
#include<iostream>
class Point
{
public:
    bool operator==(Point temp){
    if(temp.x==x&&temp.y==y) return true;
    else return false;
    }
	float x, y;
};

class Segment
{
public:

	Segment()
	{
	}
	Segment(Point _a, Point _b)
	{
		a = _a;
		b = _b;
	}
	Point getPointA()
	{
		return a;
	}
	Point getPointB()
	{
		return b;
	}
	void setPoint(Point _a, Point _b)
	{
		a = _a;
		b = _b;
	}
	float getLength()
	{
		return sqrt((a.x - b.x) * (a.x - b.x) + (a.y - b.y) * (a.y - b.y));
	}
	float getDistance(const Point &a);
private:
	Point a, b;
};

class Triangle
{
public:
	Triangle(Segment s1, Segment s2, Segment s3)
	{
		seg1 = s1;
		seg2 = s2;
		seg3 = s3;
	}
	static bool isTriangle(Segment , Segment , Segment );
	float getArea();

private:
	Segment seg1, seg2, seg3;
};
float Segment::getDistance(const Point &temp)
{
    if(a.x-b.x==0){
    float result=fabs(a.x-temp.x);
    return result;
    }else{
    float slope=(float)(a.y-b.y)/(a.x-b.x);
    float theconst=a.y-(float)slope*a.x;
    float result=fabs(slope*temp.x-temp.y+theconst)/sqrt((a.x - b.x)*(a.x - b.x)+(a.y - b.y)*(a.y - b.y));
    return result;
    }
}
bool Triangle::isTriangle(Segment s1 , Segment s2, Segment s3)
{
    if((s1.getLength()+s2.getLength())>s3.getLength()&((s2.getLength()+s3.getLength())>s1.getLength())&((s1.getLength()+s3.getLength())>s2.getLength())){
    if(s1.getPointA()==s2.getPointA()&s1.getPointB()==s3.getPointA()&s3.getPointB()==s2.getPointB()) return true;
    if(s1.getPointA()==s2.getPointA()&s1.getPointB()==s3.getPointB()&s3.getPointA()==s2.getPointB()) return true;
    if(s1.getPointA()==s2.getPointB()&s1.getPointB()==s3.getPointA()&s3.getPointB()==s2.getPointB()) return true;
    if(s1.getPointA()==s2.getPointB()&s1.getPointB()==s3.getPointB()&s3.getPointA()==s2.getPointB()) return true;
    if(s1.getPointB()==s2.getPointA()&s1.getPointA()==s3.getPointA()&s3.getPointB()==s2.getPointB()) return true;
    if(s1.getPointB()==s2.getPointA()&s1.getPointA()==s3.getPointB()&s3.getPointA()==s2.getPointB()) return true;
    if(s1.getPointB()==s2.getPointB()&s1.getPointA()==s3.getPointA()&s3.getPointB()==s2.getPointA()) return true;
    if(s1.getPointB()==s2.getPointB()&s1.getPointA()==s3.getPointB()&s3.getPointA()==s2.getPointA()) return true;
    else return false;
    }else return false;
}
float Triangle::getArea()
{
    float s=(seg1.getLength()+seg2.getLength()+seg3.getLength())/2;
    float area=sqrt(s*(s-seg1.getLength())*(s-seg2.getLength())*(s-seg3.getLength()));
    return area;
}






Overloading operators
 week6Q1
 #include<iostream>
using namespace std;
class Coordinate
{
public:
  	Coordinate(){
      x=0;
      y=0;
    }
  	Coordinate(const Coordinate &temp){
      x=temp.x;
      y=temp.y;
    }
  	Coordinate(int X,int Y){
      x=X;
      y=Y;
    }
    int getX(){
        return x;
    }
    int getY(){
        return y;
    }
    void setX(int val){
        x=val;
    }
    void setY(int val){
        y=val;
    }
    void showCoordInfo(){
        cout<<"("<<x<<", "<<y<<")"<<endl;
     }
	  bool operator>( Coordinate b){
    return  (x>b.getX()&y>b.getY());
    }
  bool operator< ( Coordinate b){
    return  (x<b.getX()&y<b.getY());
    }
    Coordinate operator+( Coordinate b){
    Coordinate result;
    result.setX(x+b.getX());
    result.setY(y+b.getY());
    return result;
    }
    Coordinate operator-(Coordinate b){
    Coordinate result;
    result.setX(x-b.getX());
    result.setY(y-b.getY());
    return result;
    }
    void operator=(Coordinate b){
    this->setX(b.getX());
    this->setY(b.getY());


    }
  
  
  
  private:
    int x;
    int y;
};
week7Q1 Geometric progression
#include<cstdio>
#include<cstdlib>
#include<iostream>
#include<math.h>
using namespace std;

class F{
private:
    double a,r;// defination of the 2 prrivate members
public:
    F(double first,double second){ // constructor with 2 parameters a and rc
        a=first;
        r=second;
    }
    F(){}
    double at(int x){
        return a*pow(r,x);
    }
    double *S(){
    if(r>-1&r<1){
        double *result=new double;
        *result=a/(1-r);
        return result;
    }else return NULL;
    }

};

int main()
{
	int j, k;
	double a, r;
	cin>>a>>r;
	F f(a, r);
	for(k = 0;k < 3;k ++)
		printf("%.2lf\n", f.at(k));
	double *s = f.S();
    if(s == NULL)
      printf("NULL\n");
  else
	printf("%.2lf\n", *s);
}

week7Q2


week7Q3
#include<iostream>
using namespace std;
class PokerCard
{
public:
    PokerCard(){}
    PokerCard(std::string s, int f)
    {
        suit = s;
        face = f;
    }
    int getface(){
        return face;
    }
    string getsuit(){
        return suit;
    }
    friend std::ostream &operator<<(std::ostream &out, const PokerCard &p)
    {
        out<<"["<<p.face<<" of "<<p.suit<<"]";
        return out;
    }
    bool operator>(PokerCard &b)
    {
        if(this->face==1&&b.getface()!=1){
            return true;
        }else if(this->face!=1&&b.getface()==1){
            return false;
        }else if(this->face==b.getface()){
            return this->suit>b.getsuit();
        }else return this->face>b.getface();
    }
    bool operator<(PokerCard &b)
    {
        if(this->face==1&&b.getface()!=1){
            return false;
        }else if(this->face!=1&&b.getface()==1){
            return true;
        }else if(this->face==b.getface()){
            return this->suit<b.getsuit();
        }else return this->face<b.getface();
    }
    bool operator==(PokerCard &b)
    {
        return (this->suit==b.getsuit()&&this->face==b.getface());
    }

private:
    std::string suit;
    int face;
};

int main()
{
    PokerCard **card = (PokerCard **)malloc(sizeof(PokerCard *) * 52);

    std::string s[] = {"spade", "heart", "diamond", "club"};
    int j, k;
    for(j = 0;j < 4;j ++)
        for(k = 1;k <= 13;k ++)
            card[j * 13 + k - 1] = new PokerCard(s[j], k);
    for(j = 0;j < 52;j ++)
    {
        for(k = 0;k < 52;k ++)
        {
            std::cout<<*(card[j])<<">"<<*(card[k])<<":"<<(*(card[j])>*(card[k]))<<std::endl;
            std::cout<<*(card[j])<<"<"<<*(card[k])<<":"<<(*(card[j])<*(card[k]))<<std::endl;
            std::cout<<*(card[j])<<"=="<<*(card[k])<<":"<<(*(card[j])==*(card[k]))<<std::endl;
        }
    }
}

week7Q4

week7Q5 Square Number
#include<stdio.h>
#include<math.h>
int main(){
	int a,b;
	while(scanf("%d%d",&a,&b)==2&&a!=0&&b!=0){
		int count;
		int i;
		for(i=a,count=0;i<=b;i++){
			if((int)sqrt((double)i)==(double)sqrt((double)i))
				count++;
		}
		printf("%d\n",count);
	}
	return 0;
}
week7Q6 Hartal
#include <iostream>
#include <set>
using namespace std;
int sum;
set <int> s;
void count(int day, int h)
{
	int w=6;//no strike on day 6
	for (int i=h; i<=day; i+=h){
		w = (w + h) % 7; //
		if (w != 6 && w != 5)
			if (s.count(i));//Returns count of occurrences of value in set
			else
				s.insert(i), sum++; // store in the container and accumulate the sum
	}
}
int main()
{
	int n, day, m, h[100];
	cin >> n;
	while (n--){
		cin >> day >> m;
		sum = 0;
		for (int i=0; i<m; i++)
			cin >> h[i], count(day, h[i]);
		cout << sum << endl;
		s.clear(); //remove all the elements of the set container
	}
return 0;
 }

week8Q1

week8Q2
#include<iostream>
class stack:private container
{
private:
    int top;
public:
    stack():container() {
    	this->top=-1;
    }
    stack(int l):container(l) {
        this->top=-1;
    }
    stack(const stack &a):container(a){
        this->top= a.top;
    }
    bool push(int data) {
        if(top==len-1) return false;
        else{
            top++;
            box[top]=data;
            return true;
        }
    }
    int *pop() {
    if(top==-1) return NULL;
    else{
        int temp=box[top];
        top--;
        return new int(temp);
        }
    }
    bool increase() {
        reallocate(len*2);
        return true;
    }
    int getLen() {
        return len;
    }
};

week8Q3
#include<iostream>
#include<string>
#include<cstdlib>
#include<algorithm>
using namespace std;
class BigNumber{
private:
    string number;
public:
    BigNumber(){}
    BigNumber(string Input_number){
        this->number=Input_number;
    }
    void Insert(int index,string str){
        this->number.insert(index,str);
    }
    void Erase(int index,int length){
        number.erase(index,length);
    }
    bool isnegtive(){
        if(number[0]=='-') return true;
        else return false;
    }
    void remove_backzero(){
        int decimal_point=-1;
        for(int i=0;i<number.length();i++){
            if(number[i]=='.') decimal_point=i;
        }
        if(decimal_point==-1) return;
        int length=number.length()-1;
        while(number[length]=='0'){
            number.erase(length,1);
            length--;
        }
        if(number[length]=='.') number.erase(length,1);
    }
    void remove_frontzero(){
        int count=0;
        while(number[count]=='0'&&number[count+2]!='.'&&number[count+1]!='.'){
            number.erase(count,1);
            count++;
        }
    }
    BigNumber operator+(BigNumber &tmp){
        if(this->isnegtive()&&!tmp.isnegtive()) {                   
             BigNumber temp(this->number);
             temp.Erase(0,1);
             return tmp-temp;
        }else if(!this->isnegtive()&&tmp.isnegtive()){              
            BigNumber temp(tmp.number);
             temp.Erase(0,1);
            return *this-temp;
        }else if(this->isnegtive()&&tmp.isnegtive()){               
            string temp1,temp2;
            temp1.assign(number,1,number.length()-1);
            temp2.assign(tmp.number,1,tmp.number.length()-1);
            BigNumber a(temp1),b(temp2),c;
            c=a+b;
            c.Insert(0,"-");
            return c;
        }else{                                                      
            string a=this->number,b=tmp.number,result;                    		    
            int a_decimalpoint=a.length(),b_decimalpoint=b.length(),i,carry=0;   
            bool a_flag=false,b_flag=false;
            for(a.length()>b.length()?i=a.length()-1:i=b.length()-1; i>=0; i--){
                if(a[i]=='.') a_decimalpoint=i,a_flag=true;
                if(b[i]=='.') b_decimalpoint=i,b_flag=true;
            }
            if(a_decimalpoint<b_decimalpoint) a.insert(a.begin(),b_decimalpoint-a_decimalpoint,'0');
            else if(a_decimalpoint>b_decimalpoint) b.insert(b.begin(),a_decimalpoint-b_decimalpoint,'0');
            if(a_flag==true&&b_flag==false) b+='.';
            else if(a_flag==false&&b_flag==true) a+='.';
            if(a.length()<b.length())  a.append(b.length()-a.length(),'0');
            else if(a.length()>b.length()) b.append(a.length()-b.length(),'0');
            for(int i=a.length()-1; i>=0; i--){
                if(a[i]=='.'){
                    result+='.';
                    continue;
                }
                int temp=(a[i]-'0'+b[i]-'0'+carry)%10;
                result+=temp+'0';
                carry=(a[i]-'0'+b[i]-'0'+carry)/10;
            }
            if(carry) result+=carry+'0';
            reverse(result.begin(),result.end());
            BigNumber result1(result);
            result1.remove_backzero();
            return result1;
        }
    }
    BigNumber operator-(BigNumber &tmp){
        if(this->isnegtive()&&!tmp.isnegtive()){                
            BigNumber temp(tmp.number);
            temp.Insert(0,"-");
            return temp+*this;
        }else if(!this->isnegtive()&&tmp.isnegtive()){          
            BigNumber temp(tmp.number);
            temp.Erase(0,1);
            return temp+*this;
        }else if(this->isnegtive()&&tmp.isnegtive()){           
            BigNumber temp(tmp.number);
            temp.Erase(0,1);
            return temp-*this;
        }else{                                                                       
            string a=this->number,b=tmp.number,result;                         			
            int a_decimalpoint=a.length(),b_decimalpoint=b.length(),i,borrow=0;      
            bool a_flag=false,b_flag=false;
            for(a.length()>b.length()?i=a.length()-1:i=b.length()-1; i>=0; i--){
                if(a[i]=='.') a_decimalpoint=i,a_flag=true;
                if(b[i]=='.') b_decimalpoint=i,b_flag=true;
            }
            if(a_decimalpoint<b_decimalpoint) a.insert(a.begin(),b_decimalpoint-a_decimalpoint,'0');
            else if(a_decimalpoint>b_decimalpoint) b.insert(b.begin(),a_decimalpoint-b_decimalpoint,'0');
            if(a_flag==true&&b_flag==false) b+='.';
            else if(a_flag==false&&b_flag==true) a+='.';
            if(a.length()<b.length())  a.append(b.length()-a.length(),'0');
            else if(a.length()>b.length()) b.append(a.length()-b.length(),'0');
            if(b>a){
                BigNumber result=tmp-*this;
                result.Insert(0,"-");
                return result;
            }
            for(int i=a.length()-1; i>=0 ;i--){
                if(a[i]=='.'){
                    result+='.';
                    continue;
                }
                int temp=((a[i]-'0')-(b[i]-'0')-borrow);
                if(temp>=0){
                    borrow=0;
                }
                else{
                    temp+=10;
                    borrow=1;
                }
                result+=temp+'0';
            }
            reverse(result.begin(),result.end());
            BigNumber  result1(result);
            result1.remove_frontzero();
            result1.remove_backzero();
            return result1;
          }
    }
    friend ostream &operator<<(ostream &out, const BigNumber &n){
        out<<n.number<<endl;
        return out;
    }
};
int main(){
    string a1,b1;
    cin>>a1>>b1;
    BigNumber a(a1),b(b1);
    cout<<a+b<<a-b;
    return 0;
}











































