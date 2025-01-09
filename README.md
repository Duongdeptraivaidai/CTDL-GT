####1.1
```c
#include<iostream>
#include<conio.h>
#include<string>
#include<iomanip>
using namespace std;
struct NhanVien {
	string HoTen;
	int NamSinh;
};

void Nhap(int& n, NhanVien NV[]) {
	cout << "\nNhap so luong: ";
	cin >> n;
	for (int i = 0; i < n; i++) {
		cout << "\nNhap ho ten: ";
		cin.ignore();
		getline(cin, NV[i].HoTen);
		cout << "\nNhap nam sinh: ";
		cin >> NV[i].NamSinh;
	}
}

void Xuat(int n, NhanVien NV[]) {
	cout << "\nDanh sach nhan vien: ";
	for (int i = 0; i < n; i++) {
		cout << "\nHo ten nguoi thu " << i + 1 << "la: ";
		cout << NV[i].HoTen;
		cout << "- nam sinh: ";
		cout << NV[i].NamSinh;
	}
}

void Xuat1(int n, NhanVien NV[]) {
	cout << "\nDanh sach nhan vien: " << endl;
	cout << "Ho ten"<<setw(30) << "Nam sinh" << endl;
	for (int i = 0; i < n; i++) {
		cout << i + 1 << ". " << NV[i].HoTen << setw(30 - NV[i].HoTen.length()) << NV[i].NamSinh << endl;
	}
	
}

int Tim(int n, NhanVien NV[], string s) {
	for (int i = 0; i < n; i++)
		if (NV[i].HoTen == s)return i;
	return -1;
}

int Tim1(int n, NhanVien NV[], string s) {
	int So = 0;
	while (NV[So + 1].HoTen == s) {
		return So + 1;
	}return -1;
}

void main() {
	int n, kq;
	string ten;
	NhanVien NV[50];
	Nhap(n, NV);
	Xuat(n, NV);
	Xuat1(n, NV);
	cin.ignore();
	
	do {
		cout << "\nBan muon tim nhan vien co ten gi?";
		getline(cin, ten);
		kq = Tim(n, NV, ten);
		if (kq == -1)cout << "Khong co";
		else cout << "NV can tim nam sinh la: " << NV[kq].NamSinh;
		cout << "\nNhan esc de thoat, nhan phim khac de tim tiep";
	} while (_getch() != 27);
}
```
####.2
```c
#include<iostream>
#include<fstream>
#include<string>
#include<conio.h>
#include<iomanip>
using namespace std;
struct ThongTin {
	string HoTen;
	int Tuoi;
};

void Xuat(ThongTin sv[], int n) {
	cout << "Ho va Ten" << setw(20) << "Tuoi" << endl;
	for (int i = 0; i < n; i++)
		cout << "\n" << sv[i].HoTen << setw(20 - sv[i].HoTen.length()) << sv[i].Tuoi;
}

void NhapFile() {
	ofstream file;
	int n;
	ThongTin sv;
	cout << "Nhap so luong sinh vien: ";
	cin >> n;
	file.open("D:\\DUONG\\main\\1.2\\Dulieu.txt", ios::app);
	for (int i = 0; i < n; i++) {
		cout << "Nhap thong tin sinh vien thu: " << i + 1;
		cin.ignore();
		cout << "\nNhap Ho va Ten sinh vien: ";
		getline(cin, sv.HoTen);
		cout << "Nhap tuoi cua sinh vien: ";
		cin >> sv.Tuoi;
		file << sv.HoTen << "\n";
		file << sv.Tuoi << "\n";
	}
	file.close();
}

void docFile(ThongTin sv[], int& n) {
	ifstream file;
	string t;
	file.open("DuLieu.txt");
	n = 0;
	while (file) {
		getline(file, sv[n].HoTen);
		file >> sv[n].Tuoi;
		getline(file, t);
		n++;
	}
	n--;
	file.close();
}

int main() {
	ThongTin sv[10];
	int n;
	NhapFile();
	docFile(sv,n);
	Xuat(sv,n);
	_getch(); 
}
```
####1.3 (chua xong)
```c
#include<iostream>
#include<conio.h>
#include<string>
#include<iomanip>
using namespace std;
struct HocSinh {
	string HoTen;
	float dLT, dTH;

};

void hoanvi(int& a, int &b) {
	int temp = b;
	b = a;
	a = temp;
	return hoanvi(a,b);
}

void Nhap(int& n, HocSinh SV[]) {
	cout << "Nhap so luong hoc sinh: ";
	cin >> n;
	for (int i = 0; i < n; i++) {
		cout << "\nNhap ho ten: ";
		cin.ignore();
		getline(cin, SV[i].HoTen);
		cout << "\nNhap diem LT: ";
		cin >> SV[i].dLT;
		cout << "\nNhap diem TH; ";
		cin >> SV[i].dTH;
	}
}

void Xuat(int n, HocSinh SV[]) {
	cout << "\nDanh sach hoc sinh: ";
	for (int i = 0; i < n; i++) {
		cout << "\nHo ten hoc sinh thu " << i + 1 << "la: ";
		cout << SV[i].HoTen << endl;
		cout << "diem ly thuyet la: ";
		cout << SV[i].dLT;
		cout << "diem thuc hanh la: ";
		cout << SV[i].dTH;
	}
}

int Tim(int n, HocSinh SV[], string s) {
	for (int i = 0; i < n; i++)
		if (SV[i].HoTen == s)return i;
	return -1;
}


int main() {
	int n,kq;
	string HoTen;
	HocSinh SV[100];
	Nhap(n, SV);
	Xuat(n, SV);
	cin.ignore();


do {
	cout << "\nBan muon tim hoc sinh co ten gi?";
	getline(cin, HoTen);
	kq = Tim(n, SV, HoTen);
	if (kq == -1)cout << "Khong co";
	else { cout << "NV can tim diem ly thuyet la: " << SV[kq].dLT;
	cout << "NV can tim diem thuc hanh la: " << SV[kq].dTH;
	}
	cout << "\nNhan so khac 1,2,3,4 de thoat, nhan phim 1,2,3,4 de tim tiep";
} while (_getch() != 27);
}

```
