# Vcomply-
test in C++


#include <bits/stdc++.h>
using namespace std;

struct date{
    int day,month,year;
};

int btw(struct date d1,struct date d2,struct date p){
    bool k,l;
    if(d1.year>p.year) return 1;
    if(d2.year<p.year) return 2;
    if(d1.year==p.year){
        if(d1.month>p.month) return 1;
        else if(d1.month==p.month){
            if(d1.day>p.day) return 1;
        }
    }
    if(d2.year==p.year){
        if(d2.month<p.month) return 2;
        else if(d2.month==p.month){
            if(d2.day<p.day) return 2;
        }
    }
    return 0;
}

void isSlotAvailable(struct date al[][2],struct date rl[2],int n){
    int i=0;
    for(;i<n;i++){
        if(btw(al[i][0],al[i][1],rl[0])==btw(al[i][0],al[i][1],rl[1])!=0) continue;
        else break;
    }
    if(i==n) cout<<"true"<<endl;
    else cout<<"false"<<endl;
}

int main() {
	int n;
	cin>>n;
	string A="";
	getline(cin,A);
	struct date al[n][2];
	for(int i=0;i<n;i++){
	    getline(cin,A);
	    stringstream S(A);
	    string B;
	    int count=0;
	    while(S>>B){
	        count++;
	        if(count==4){
	            cout<<i<<" "<<B<<endl;
	            al[i][0].day=stoi(B.substr(0,2));
	            al[i][0].month=stoi(B.substr(3,2));
	            al[i][0].year=stoi(B.substr(6,4));
	        }
	        else if(count==6){
	            al[i][1].day=stoi(B.substr(0,2));
	            al[i][1].month=stoi(B.substr(3,2));
	            al[i][1].year=stoi(B.substr(6,4));
	        }
	        B="";
	    }
	}
	struct date rl[2];
	getline(cin,A);
	stringstream S(A);
	string B;
	int count=0;
	while(S>>B){
	        count++;
	        if(count==2){
	            rl[0].day=stoi(B.substr(0,2));
	            rl[0].month=stoi(B.substr(3,2));
	            rl[0].year=stoi(B.substr(6,4));
	            //cout<<rl[0].day<<" "<<rl[0].year<<endl;
	        }
	        else if(count==4){
	            cout<<count<<" "<<B<<endl;
	            rl[1].day=stoi(B.substr(0,2));
	            rl[1].month=stoi(B.substr(3,2));
	            rl[1].year=stoi(B.substr(6,4));
	        }
	        B="";
	}
	cout<<al[0][0].day<<" "<<al[0][1].year<<endl;
	isSlotAvailable(al,rl,n);
	return 0;
}
