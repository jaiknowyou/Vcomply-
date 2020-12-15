# Vcomply-
test


#include <bits/stdc++.h>
using namespace std;

struct date{
    int day,month,year;
};

bool btw(struct date d1,struct date d2,struct date p){
    bool k,l;
    if(d1.year>p.year||d2.year<p.year) return false;
    else if(d1.year==p.year){
        if(d1.month>p.month) return false;
        else if(d1.month==p.month){
            if(d1.day>=p.day) return false;
        }
    }
    if(d2.year==p.year){
        if(d2.month<p.month) return false;
        else if(d1.month==p.month){
            if(d1.day<=p.day) return false;
        }
    }
    return true;
}

void ans(int al[][2],int n){
    int i=0;
    for(;i<n;i++){
        if(!btw(al[i][0],al[i][1],al[n][0])&&!btw(al[i][0],al[i][1],al[n][1])) continue;
        else break;
    }
    if(i==n) cout<<"true"<<endl;
    else cout<<"false"<<endl;
}

int main() {
	int n;
	cin>>n;
	string A;
	struct date al[n+1][2];
	for(int i=0;i<=n;i++){
	    getline(cin,A);
	    stringstream S(A);
	    string B;
	    int count=0;
	    while(S>>B){
	        count++;
	        if(count==4){
	            al[i][0].day=stoi(B.substr(0,2));
	            al[i][0].month=stoi(B.substr(3,2));
	            al[i][0].year=stoi(B.substr(6,4));
	        }
	        else if(count==6){
	            al[i][1].day=stoi(B.substr(0,2));
	            al[i][1].month=stoi(B.substr(3,2));
	            al[i][1].year=stoi(B.substr(6,4));
	        }
	    }
	}
	ans(al,n);
	return 0;
}
