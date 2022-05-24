### 


@Type something…































































Kill code

//uva12019
#include <iostream>
using namespace std;

int main()
{
	char week[10][10] = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};
	int month[] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
	int n;

	cin >> n;
	while(n--)
	{
		int mm, dd;
		cin >> mm >> dd;

		int w = 4;
		for(int i = 1; i < mm; i++)
			w += month[i-1];

		w = (w + dd) % 7;
		cout << week[w] << endl;
	}
	return 0;
}
				       
/uva10921
#include <iostream>
#include <string>
using namespace std;

int main(){
	string s;
	int cap, hyphen;
	while(cin >> s){
		cap = 0;
		hyphen = 0;
		for(int i = 0 ; i < s.length() ; i++){
            if(s[i] == '0')
                cout << 0;
			else if(s[i] == '1')
				cout << 1;
			else if(s[i] == '-'){
				cout << '-';
				hyphen++;
			}
			else if('A'<=s[i] && s[i]<='C'){
				cout << 2;
				cap++;
			}
			else if('D'<=s[i] && s[i]<='F'){
				cout << 3;
				cap++;
			}
			else if('G'<=s[i] && s[i]<='I'){
				cout << 4;
				cap++;
			}
			else if('J'<=s[i] && s[i]<='L'){
				cout << 5;
				cap++;
			}
			else if('M'<=s[i] && s[i]<='O'){
				cout << 6;
				cap++;
			}
			else if('P'<=s[i] && s[i]<='S'){
				cout << 7;
				cap++;
			}
			else if('T'<=s[i] && s[i]<='V'){
				cout << 8;
				cap++;
			}
			else if('W'<=s[i] && s[i]<='Z'){
				cout << 9;
				cap++;
			}
		}
		cout << " " << cap << " " << hyphen <<endl;
	}
	return 0;
}				       


//uva725
#include <iostream>
#include <cstdlib>
#include <iomanip>
using namespace std;

bool isnonrepeat(int a, int b){
    int n[10];
    if (a < 10000 && b < 10000)return false;
    for(int i = 0; i < 10; ++i)n[i] = 0;
    if (a < 10000 || b < 10000)n[0] = 1;
    while (a > 0){
        if (n[a % 10] == 1)return false;
        else n[a % 10] = 1;
        a /= 10;
    }
    while (b > 0){
        if (n[b % 10] == 1)return false;
        else n[b % 10] = 1;
        b /= 10;
    }
    return true;
}

int main(){
    int n;
    int a;
    bool ans;
    bool start = true;

    while (cin >> n){
        if (n == 0)break;
        if (!start)cout << endl;
        start = false;
        ans = false;
        for (int i = 1234; i < 49876; ++i){
            a = i * n;
            if (a > 99999)continue;
            else {
                if (isnonrepeat(a, i)){
                    ans = true;
                    cout << setw(5) << setfill('0') << a;
                    cout << " / ";
                    cout << setw(5) << setfill('0') << i;
                    cout << " = " << n << endl;
                }
            }
        }
        if (!ans){
            cout << "There are no solutions for " << n << "." << endl;
        }
	}
	return 0;
}

//uva11489
#include <iostream>
#include <vector>
#include <string> 
using namespace std;

int main(){

    int n;
    int nowcase = 0;
    string s;

    cin >> n;
    for(int i=0 ; i < n ; i++){
        cin >> s;
        nowcase++;
        int sum = 0;
        int counter = 0;
        vector<int> num;
        for(int j=0 ; j < s.length() ; j++){
            num.push_back(s[j]-'0');
            sum += s[j]-'0';
        }
        
        for(int j=0 ; j < num.size(); j++){
            if(num[j]%3 == 0) counter++;
        }

        if(sum%3 == 0){
            if(counter%2 == 0)
				cout << "Case " << nowcase << ": T" << endl;
            else
				cout << "Case " << nowcase << ": S" << endl;
        }
        else{
            for(int j=0 ; j < num.size() ; j++){
                if((sum-num[j])%3 == 0){
                    if(counter%2 == 0)
						cout << "Case " << nowcase << ": S" << endl;
                    else 
						cout << "Case " << nowcase << ": T" << endl;
                    break;
                }
                else if(j == num.size()-1){
                    cout << "Case " << nowcase << ": T" << endl;
                    break;
                }
            }
        }
    }
}

//uva12218
#include <iostream>
#include <string>
#include <cstring>
#include <cmath>
#include <set>
#include <algorithm>
using namespace std;

int main(){
	// prime table, take really much time here
	static bool prime[9999999+1];
	fill(prime,prime + 9999999+1, true);
	prime[0] = prime[1] = false;
	double bound = sqrt(9999999.0) + 0.5;
	for(int i=2 ; i*i < 9999999+1 ; ++i){
		for(int j=2 ; j*i < 9999999+1 ; ++j){
			prime[i*j] = false;
		}
	}
	
	int n;
	cin >> n;
	while(n--){
		set<int> ansSet;
		string input;
		cin >> input;
		sort(input.begin(),input.end());
		// test bit by bit ( 2^n )
		for(int i=0 ; i < (1 << input.size()) ; ++i){
			string testCase = "";
			for(int j=0 ; j < input.size() ; ++j)
				if(i & (1 << j)) testCase += input[j];
			do{
				int num = atoi(testCase.c_str());
				if(!prime[num]) continue;
				if(ansSet.count(num)) continue;
				ansSet.insert(num);
			}while(next_permutation(testCase.begin(),testCase.end()));
		}
		cout << ansSet.size() << endl;
	}
	
	return 0;
} 

//uva11495
#include <iostream>
using namespace std;

long long merge(int *P, int left, int mid, int right){
	int *tmp = new int[right - left + 1];
	long long sum = 0;
	
	int iLeft = left;
	int iRight = mid+1;
	int iMerge = 0;
	
	// the middle reverse numbers
	while(iLeft <= mid && iRight <= right){
		if(P[iLeft] <= P[iRight]){
			tmp[iMerge++] = P[iLeft++];
		}else{
			tmp[iMerge++] = P[iRight++]; 
			sum += mid - iLeft + 1;      // key point
		}
	}
	while(iLeft <= mid)
		tmp[iMerge++] = P[iLeft++];
		
	while(iRight <= right)
		tmp[iMerge++] = P[iRight++];
		
	for(int i = left ; i <= right ; ++i)
		P[i] = tmp[i - left];
		
	delete [] tmp;
	return sum;
}

long long mergesort(int *P, int left, int right){
	long long sum=0;
	// reverse number = left reverse numbers + right reverse numbers + the middle reverse numbers
	if(left < right){
		int mid = (left + right) / 2;
		sum = mergesort(P, left, mid);
		sum += mergesort(P, mid+1, right);
		sum += merge(P, left, mid, right);
	}
	return sum;
}

int main(){
	int n;
	while(cin >> n && n){	
		int *P = new int[n];	
		for(int i=0 ; i < n ; ++i)  // read in permutation
			cin >> P[i];
			
		long long ans = mergesort(P,0,n-1);  // count the reverse order number

		if(ans % 2 == 0)
			cout << "Carlos " << ans << endl;
		else
			cout << "Marcelo " << ans << endl;
		delete [] P;
	}
	return 0;
}

//uva709
#include <iostream>
#include <string> 
using namespace std;

int main(){	
	int width;
	while(cin >> width && width){
		cin.ignore();
		
		string words[10050];
		int sumLength[10050];
		int dp[10050];
		int endWord[10050];
		
		string tmp;
		int wordCnt = 1;  // not use 0
		// read the paragraph
		while(getline(cin,tmp) && tmp.size() > 0){
			// split ( including a long space
			int begin = 0;
			int end = 0;
			while(end != -1){
				end = tmp.find(' ',begin);
				words[wordCnt] = tmp.substr(begin,end - begin);
				if(words[wordCnt].size() != 0) ++wordCnt;
				begin = end+1;
			}
		}
		
		// calculate the length after pick each word
		sumLength[0] = 0;
		for(int i = 1 ; i < wordCnt ; ++i)
			sumLength[i] = sumLength[i-1] + words[i].size();
		
		// dp from right to left
		dp[wordCnt] = 0;  // the dp initial state
		// calculate the best position to put each remaining word
		for(int i = wordCnt-1 ; i > 0 ; --i){  // i: curWord
			dp[i] = dp[i+1] + 500;  // penalty of one word occupying one line
			endWord[i] = i;         // start from words[i] ends at words[i]
			
			// try to pick in as more words as possible( ... �B are�Bareactually�Bareactuallyconsidering.) 
			for(int j=i+1 ; j < wordCnt ; ++j){
				if(sumLength[j] - sumLength[i-1] + j - i > width) break;  // can not be a row (no space for ' ')
				int totalSpace = width - (sumLength[j] - sumLength[i-1]); // total extra space to fill
				int avgSpace = totalSpace / (j-i);                        // (average) middle space after between i to j words
				int extraSpace = totalSpace - avgSpace*(j-i);             // number of extra space
				// penalty of one row:  (number of avgSpace)*(length of space)^2 + (number of extra space)*(length of extra space)^2
				// length of space = midAvgSpace - 1 (that is, if midAvgSpace = 4, then penalty is 3^2)
				// length of extra space = midAvgSpace
				int cost = (j-i-extraSpace)*(avgSpace-1)*(avgSpace-1) + (extraSpace)*avgSpace*avgSpace;
				if( dp[i] >= dp[j+1] + cost ){
					dp[i] = dp[j+1] + cost;
					endWord[i] = j;    // start from words[i] ends at words[j]
				}
			}
		}
		
		// print the paragraph
		int curWord = 1;
		while(curWord < wordCnt){
			if(endWord[curWord] > curWord){
				int i = curWord;
				int j = endWord[i]/* - 1*/;
				int totalSpace = width - (sumLength[j] - sumLength[i-1]);
				int avgSpace = totalSpace / (j-i);
				int extraSpace = totalSpace - avgSpace*(j-i);
				
				int count = 0;         // how many avgSpace have been printed
				cout << words[i];      // start from words[i] ends at words[j]
				for(int nextWord = i+1 ; nextWord <= j ; ++nextWord){
					// print "avgSpace" space
					for(int space = 0 ; space < avgSpace ; ++space)
						cout << " ";
					if(++count > (j-i-extraSpace))
						cout << " ";
					cout << words[nextWord];					
				}
				cout << endl;
			}else{
				// if the word occupies one whole line
				cout << words[curWord] << endl;
			}
			curWord = endWord[curWord] + 1;
		}
		cout << endl;
		
	}
	return 0;
}






























