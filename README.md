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
#5.2
```c
#include<iostream>
#include<string>
#include<fstream>
#include<conio.h>
using namespace std;

 void Swap(int& a, int& b) {
	int temp = a;
	a = b;
	b = temp;
}
 void Swap1(string& a, string& b) {
	string temp = a;	
	a = b;
	b = temp;
}

 struct BAIHAT {
	string ten;
	int view,nam;
};   

 void xuat(BAIHAT a[], int n) {
	for (int i = 0; i < n; i++) {
		cout << "Sinh vien thu " << i + 1 << endl;
		cout << "Nam phat hanh: " << a[i].nam << endl; //nam phat hanh mssv
		cout << "View: " << a[i].view << endl; //view dtoan
	}
}

 void nhapFile(BAIHAT a[], int& n) {
	ofstream file;
	file.open("0306241102.txt", ios::app);
	do {
		cout << "Nhap so luong bai hat: ";
		cin >> n;
	} while (n <= 0);
	for (int i = 0; i < n; i++) {
		cout << "Nhap bai hat thu " << i + 1 << endl;
		cin.ignore();
		cout << "Nhap ten bai hat: ";
		getline(cin, a[i].ten);
		cin.ignore();
		do {
			cout << "Nhap nam phat hanh: ";
			cin >> a[i].nam;
			cin.ignore();
		} while (a[i].nam < 1);
		do {
			cout << "Nhap diem toan: ";
			cin >> a[i].view;
			cin.ignore();
		} while (a[i].view <= 0);
		file << "Ten bai hat: " << a[i].ten << endl;
		file << "Nam phat hanh: " << a[i].nam << endl;
		file << "view: " << a[i].view << endl;
	}
	file.close();


}



 void docFile(BAIHAT a[], int& n) {
	ifstream file;
	string s;
	file.open("0306241102.txt");
	n = 0;
	while (file) {
		getline(file, a[n].ten);
		cout << a[n].ten<< endl;
		file >> a[n].nam;
		file >> a[n].view;
		file.ignore();
		getline(file, s);
		n++;

	}
	n--;
	file.close();

}

int SearchMaxView(BAIHAT a[], int &n) {
	int max = a[0].view;
	int vt = 0;
	for (int i = 0; i < n; i++) {
		if (a[i].view > max) {
			max = a[i].view;
			vt = i;
		}
	}
	return vt;
 }

int SearchMinView(BAIHAT a[], int &n) {
	int min = a[0].view;
	int vt = 0;
	for (int i = 0; i < n; i++) {
		if (a[i].view <  min) {
			min = a[i].view;
			vt = i;
		}
	}
	cout << "Bai Hat co so View cao nhat la: ";
	return vt;
}

 void SapXepTangDanNam(BAIHAT a[], int n) {
	for (int i = 0; i < n - 1; i++) {
		for (int j = i + 1; j < n; j++) {
			if (a[i].nam > a[j].nam) {
				Swap1(a[i].ten, a[j].ten);
				Swap(a[i].nam, a[j].nam);
				Swap(a[i].view, a[j].view);
			}
		}
	}
}

 void SapXepGiamDanView(BAIHAT a[], int n) {
	for (int i = 0; i < n - 1; i++) {
		for (int j = i + 1; j < n; j++) {
			if (a[i].view < a[j].view) {
				Swap1(a[i].ten, a[j].ten);
				Swap(a[i].nam, a[j].nam);
				Swap(a[i].view, a[j].view);
				
			}
		}
	}
}

int SearchByName(BAIHAT a[], int n, string name) {
	for (int i = 0; i < n; i++) {
		if (a[i].ten == name) {  // Nếu tên bài hát khớp
			return i;  // Trả về chỉ mục của bài hát
		}
	}
	return -1;  //neu khong tim thay
}





int main() {
	BAIHAT a[100];
	int n;
	int chose;
	int minIndex = SearchMinView(a, n);
	int maxIndex = SearchMaxView(a, n);
	int x;
	
	do {
		cout << "1. Nhap file" << endl;
		cout << "2. Doc file" << endl;
		cout << "3. Tim bai hat co luot view cao nhat: " << endl;
		cout << "4. Tim bai hat co luot view thap nhat:" << endl;
		cout << "5. Tim bai hat theo ten nhap vao:  " << endl;
		cout << "6. Sap xep tang dan theo Nam phat hanh:  " << endl;
		cout << "7. Sap xep gian dan theo So luot View" << endl;
		cout << "8. Nhan ESC de thoat!" << endl;

		cout << "Chon: ";
		cin >> chose;
		string x;
		switch(chose) 
		{
			case 1:nhapFile(a, n); break;
			case 2:docFile(a, n); break;
			case 3:  // Tìm chỉ mục của bài hát có view cao nhất
				cout << "Bai hat co so luong view cao nhat:" << endl;
				cout << "Ten bai hat: " << a[maxIndex].ten << endl;
				cout << "Nam phat hanh: " << a[maxIndex].nam << endl;
				cout << "View: " << a[maxIndex].view << endl; break;

			case 4: // Tìm bài hát có view thấp nhất
				cout << "Bai hat co so luong view thap nhat:" << endl;
				cout << "Ten bai hat: " << a[minIndex].ten << endl;
				cout << "Nam phat hanh: " << a[minIndex].nam << endl;
				cout << "View: " << a[minIndex].view << endl; break;

			case 5: {
				cin.ignore();  // Để bỏ qua ký tự '\n' còn lại trong bộ đệm sau khi nhập chon
				cout << "Nhap ten bai hat can tim: ";
				getline(cin, x);  // Nhập tên bài hát
				int index = SearchByName(a, n, x);  // Tìm bài hát theo tên
				if (index != -1) {
					// Nếu tìm thấy bài hát
					cout << "Bai hat tim duoc:" << endl;
					cout << "Ten bai hat: " << a[index].ten << endl;
					cout << "Nam phat hanh: " << a[index].nam << endl;
					cout << "View: " << a[index].view << endl;
				}
				else {
					cout << "Khong tim thay bai hat voi ten '" << x << "'!" << endl;
				}
			}break;

			case 6:SapXepTangDanNam(a, n); xuat(a, n); break;
			case 7:SapXepGiamDanView(a, n); xuat(a, n); break;
		}
	

	} while (_getch()!=27);

}
```
