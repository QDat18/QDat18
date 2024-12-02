#include <ctype.h>
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#define MAX 100
// Khai bao cau truc Nhan vien
typedef struct NhanVien {
  char MaNV[10];
  char HoTen[50];
  Date NgaySinh;
  char GioiTinh[4];
  char DiaChi[100];
  char SoDienThoai[15];
  char ChucVu[30];
  char Email[50];
  float LuongCoBan;
} NhanVien;
// Khai bao cau truc danh sach Nhan vien
typedef struct NhanVienList {
  NhanVien NV;
  struct NhanVienList *pNext;
} NhanVienList;
// Khai bao cau truc Kho
typedef struct Kho {
  Bike bike;
  char MaKho[10];
  char TenKho[50];
  char DiaChi[100];
  char SoDienThoai[15];
} Kho;
// Khai bao cau truc danh sach Kho
typedef struct KhoList {
  Kho K;
  struct KhoList *pNext;
} KhoList;
// Khai bao cau truc NCC
typedef struct NCC {
  char MaNCC[10];
  char TenNCC[50];
  char DiaChi[100];
  char SoDienThoai[15];
} NCC;
// Khai bao cau truc danh sach NCC
typedef struct NCCList {
  NCC N;
  struct NCCList *pNext;
} NCCList;
// Khai bao cau truc Thong ke
typedef struct ThongKe {
  char MaNV[10];
  char TenNV[50];
  char ChucVu[30];
  float TongDoanhThu;
  HoaDon hoaDon;          
  HoaDonBan hoaDonBan;
  HoaDonNhap hoaDonNhap;
} ThongKe;

// Khai bao cau truc danh sach Thong ke
typedef struct TkList {
  ThongKe T;
  struct TkList *pNext;
} TkList;
// Khai bao ham tao danh sach Nhan vien moi
     
typedef struct {
          int Ngay;
          int Thang;
          int Nam;
} Date;

typedef struct {
          char ma[10];
          char ten[30];
          char SDT[20];
          char diaChi[100];
          char email[50];
} identifier;

typedef struct {
          char maXe[10];
          char tenXe[30];
          char mauSac[20];
          int soLuong;
          float donGia;
          int tinhTrang;
} Bike;

typedef struct bikeNode {
          Bike bike;
          struct bikeNode *next;
} BikeNode;

typedef struct {
          BikeNode *head;
} BikeList;

typedef struct {
          Kho kho;
          struct khoNode *next;
} KhoNode;

typedef struct {
          char MaNCC[10];
          char TenNCC[30];
          char diaChi[50];
          char email[50];
          char SDT[15];
} NhaCC;

typedef struct nccNode {
          NhaCC ncc;
          struct nccNode *next;
} NccNode;

typedef struct {
          NccNode *head;
} NccList;

typedef struct {
          identifier ch;
} CuaHang;

typedef struct cuaHangNode {
          CuaHang ch;
          struct cuaHangNode *next;
} CuaHangNode;

typedef struct {
          CuaHangNode *head;
} CuaHangList;

typedef struct nvNode {
          NhanVien nv;
          struct nvNode *next;
} NhanVienNode;

typedef struct {
          identifier kh;
          char gioiTinh[5];
          Date ngaySinh;
          Date ngayMua;
} KhachHang;

typedef struct khachHangNode {
          KhachHang kh;
          struct khachHangNode *next;
} KhachHangNode;

typedef struct {
          KhachHangNode *head;
} KhachHangList;

typedef struct {
          char maHD[10];
          double thanhTien;
          Date ngayGiaoDich;
} HoaDon;

typedef struct {
          HoaDon hoaDonNhap;
          NhaCC ncc;
          Bike bike;
          double giaNhap;
          int soLuongNhap;
          float TongtienNhap;
          Kho kho;
} HoaDonNhap;

typedef struct {
          Bike bike;
          HoaDon hoaDonBan;
          KhachHang kh;
          int soLuongBan;
          double donGia;
          float TongTienBan; 
} HoaDonBan;
typedef struct tkNode {
          ThongKe tk;
          struct tkNode *next;
} TkNode;

// Function declaration

BikeNode *createBikeNode(Bike bike);
KhoNode *createKhoNode(Kho kho);
NccNode *createNccNode(NhaCC ncc);
CuaHangNode *createCuaHangNode(CuaHang ch);
NhanVienNode *createNhanVienNode(NhanVien nv);
KhachHangNode *createKhachHangNode(KhachHang kh);
HoaDonNhap *createHoaDonNhap(HoaDonNhap hoaDonNhap);
HoaDonBan *createHoaDonBan(HoaDonBan hoaDonMua);
TkNode *createTkNode(ThongKe tk);
void addTail(BikeList *l, BikeNode *newNode);
void insertBike(BikeList *l, const char *FilenameBike);
void insertKho(KhoList *l, const char *FilenameKho);
void insertNcc(NccList *l, const char *FilenameNcc);
void insertCuaHang(CuaHangList *l, const char *FilenameCuaHang);
void insertNhanVien(NhanVienList *l, const char *FilenameNhanVien);
void insertKhachHang(KhachHangList *l, const char *FilenameKhachHang);
void insertHoaDonNhap(HoaDonNhap *l, const char *FilenameHoaDonNhap);
void insertHoaDonBan(HoaDonBan *l, const char *FilenameHoaDonMua);
void insertThongKe(ThongKe *l, const char *FilenameThongKe);
void displayHeaders();
void displayBike(Bike bike);
void displayKhoHeaders();
void displayKho(Kho kho);
void displayNccHeaders();
void displayNcc(NhaCC ncc);
void displayCuaHangHeaders();
void displayCuaHang(CuaHang ch);
void displayNhanVienHeaders();
void displayNhanVien(NhanVien nv);
void displayKhachHangHeaders();
void displayKhachHang(KhachHang kh);
void menuXe(BikeList *bike, const char *FilenameBike);
void MenuKho(KhoList *l, const char *FilenameKho);
void MenuNcc(NccList *l, const char *Filenamencc);
void menuCuaHang(CuaHangList *l, const char *FilenameCuaHang);
void MenuNhanVien(NhanVienList *l, const char *FilenameNhanVien);
void menuKhachHang(KhachHangList *l, const char *FilenameKhachHang);
void menuHoaDonNhap(HoaDonNhap *l, const char *FilenameHoaDonNhap);
void menuHoaDonBan(HoaDonBan *l, const char *FilenameHoaDonMua);
void menuThongKe(TkList *l, const char *FilenameThongKe);

NhanVienList *CreateNhanVienList() {
  NhanVienList *pHead = NULL;
  return pHead;
}
// Khai bao ham them Nhan vien vao danh sach Nhan vien
NhanVienList *AddNhanVien(NhanVienList *pHead, NhanVien NV) {
  NhanVienList *pNew = (NhanVienList *)malloc(sizeof(NhanVienList));
  if (pNew == NULL) {
    printf("Bo nho khong du!");
    return pHead;
  }
  pNew->NV = NV;
  pNew->pNext = pHead;
  pHead = pNew;
  return pHead;
}
// Khai bao ham tao danh sach Kho moi
KhoList *CreateKhoList() {
  KhoList *pHead = NULL;
  return pHead;
}
// Khai bao ham them Kho vao danh sach Kho
KhoList *AddKho(KhoList *pHead, Kho K) {
  KhoList *pNew = (KhoList *)malloc(sizeof(KhoList));
  if (pNew == NULL) {
    printf("Bo nho khong du!");
    return pHead;
  }
  pNew->K = K;
  pNew->pNext = pHead;
  pHead = pNew;
  return pHead;
}
// Khai bao ham tao danh sach NCC moi
NCCList *CreateNCCList() {
  NCCList *pHead = NULL;
  return pHead;
}
// Khai bao ham them NCC vao danh sach NCC
NCCList *AddNCC(NCCList *pHead, NCC N) {
  NCCList *pNew = (NCCList *)malloc(sizeof(NCCList));
  if (pNew == NULL) {
    printf("Bo nho khong du!");
    return pHead;
  }
  pNew->N = N;
  pNew->pNext = pHead;
  pHead = pNew;
  return pHead;
}
// Khai bao ham tao danh sach Thong ke moi
TkList *CreateTkList() {
  TkList *pHead = NULL;
  return pHead;
}
// Khai bao ham them Thong ke vao danh sach Thong ke
TkList *AddTk(TkList *pHead, ThongKe T) {
  TkList *pNew = (TkList *)malloc(sizeof(TkList));
  if (pNew == NULL) {
    printf("Bo nho khong du!");
    return pHead;
  }
  pNew->T = T;
  pNew->pNext = pHead;
  pHead = pNew;
  return pHead;
}
// Khai bao ham doc du lieu tu file cho danh sach Nhan vien
NhanVienList *ReadNhanVienFromFile(const char *Filename) {
  NhanVienList *pHead = CreateNhanVienList();
  FILE *fp = fopen(Filename, "r");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return pHead;
  }
  NhanVien NV;
  while (fscanf(fp, "%[^,],%[^,],%[^,],%[^,],%[^,],%[^,],%[^,],%f\n", NV.MaNV,
                NV.HoTen, NV.NgaySinh, NV.GioiTinh, NV.DiaChi, NV.SoDienThoai,
                NV.ChucVu, &NV.LuongCoBan) != EOF) {
    pHead = AddNhanVien(pHead, NV);
  }
  fclose(fp);
  return pHead;
}
// Khai bao ham doc du lieu tu file cho danh sach Kho
KhoList *ReadKhoFromFile(const char *Filename) {
  KhoList *pHead = CreateKhoList();
  FILE *fp = fopen(Filename, "r");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return pHead;
  }
  Kho K;
  while (fscanf(fp, "%[^,],%[^,],%[^,],%[^,\n]", K.MaKho, K.TenKho, K.DiaChi,
                K.SoDienThoai) != EOF) {
    pHead = AddKho(pHead, K);
  }
  fclose(fp);
  return pHead;
}
// Khai bao ham doc du lieu tu file cho danh sach NCC
NCCList *ReadNCCFromFile(const char *Filename) {
  NCCList *pHead = CreateNCCList();
  FILE *fp = fopen(Filename, "r");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return pHead;
  }
  NCC N;
  while (fscanf(fp, "%[^,],%[^,],%[^,],%[^,\n]", N.MaNCC, N.TenNCC, N.DiaChi,
                N.SoDienThoai) != EOF) {
    pHead = AddNCC(pHead, N);
  }
  fclose(fp);
  return pHead;
}
// Khai bao ham doc du lieu tu file cho danh sach Thong ke
TkList *ReadTkFromFile(const char *Filename) {
  TkList *pHead = CreateTkList();
  FILE *fp = fopen(Filename, "r");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return pHead;
  }
  ThongKe T;
  while (fscanf(fp, "%[^,],%[^,],%[^,],%d,in%f\n", T.MaNV, T.TenNV, T.ChucVu,
                &T.SoLuongBanHang, &T.TongDoanhThu) != EOF) {
    pHead = AddTk(pHead, T);
  }
  fclose(fp);
  return pHead;
}

BikeNode *createBikeNode(Bike bike) {
  BikeNode *newNode = (BikeNode *)malloc(sizeof(BikeNode));
  newNode->bike = bike;
  newNode->next = NULL;
  return newNode;
}

KhoNode *createKhoNode(Kho kho) {
  KhoNode *newNode = (KhoNode *)malloc(sizeof(KhoNode));
  newNode->kho = kho;
  newNode->next = NULL;
  return newNode;
}

NccNode *createNccNode(NhaCC ncc) {
  NccNode *newNode = (NccNode *)malloc(sizeof(NccNode));
  newNode->ncc = ncc;
  newNode->next = NULL;
  return newNode;
}

CuaHangNode *createCuaHangNode(CuaHang ch) {
  CuaHangNode *newNode = (CuaHangNode *)malloc(sizeof(CuaHangNode));
  newNode->ch = ch;
  newNode->next = NULL;
  return newNode;
}

NhanVienNode *createNhanVienNode(NhanVien nv) {
  NhanVienNode *newNode = (NhanVienNode *)malloc(sizeof(NhanVienNode));
  newNode->nv = nv;
  newNode->next = NULL;
  return newNode;
}

KhachHangNode *createKhachHangNode(KhachHang kh) {
  KhachHangNode *newNode = (KhachHangNode *)malloc(sizeof(KhachHangNode));
  newNode->kh = kh;
  newNode->next = NULL;
  return newNode;
}

TkNode *createTkNode(ThongKe tk) {
  TkNode *newNode = (TkNode *)malloc(sizeof(TkNode));
  newNode->tk = tk;
  newNode->next = NULL;
  return newNode;
}

void addTail(BikeList *l, BikeNode *newNode) {
  if (l->head == NULL) {
    l->head = newNode;
  } else {
    BikeNode *current = l->head;
    while (current->next != NULL) {
      current = current->next;
    }
    current->next = newNode;
  }
}

// Function insert
void initList(BikeList *bikeList) {
  bikeList->head = NULL;
}

void insertBike(BikeList *l, const char *FilenameBike) {
          Bike bike;
          printf("\nNhap ma xe: ");
          scanf("%s", bike.maXe);
          printf("Nhap ten xe: ");
          scanf("%s", bike.tenXe);
          printf("Nhap so luong xe: ");
          scanf("%d", &bike.soLuong);
          printf("Nhap mau sac xe: ");
          scanf("%s", bike.mauSac);
          printf("Nhap tinh trang xe (1: Moi, 0: Cu): ");
          scanf("%d", &bike.tinhTrang);
          printf("Nhap don gia: ");
          scanf("%f", &bike.donGia);

          BikeNode *newNode = createBikeNode(bike);
          addTail(l, newNode);

          FILE *file = fopen(FilenameBike, "a");
          if (file == NULL) {
            printf("Khong the mo file.\n");
            return;
          }
          fprintf(file, "%s,%s,%d,%s,%d,%.2f\n", bike.maXe, bike.tenXe,
                  bike.soLuong, bike.mauSac, bike.tinhTrang, bike.donGia);
          fclose(file);
          printf("Da them xe va luu vao file.\n");
}

void insertKho(KhoList *l, const char *FilenameKho) {
          Kho kho;
          printf("\nNhap ma kho: ");
          scanf("%s", kho.MaKho);
          printf("Nhap ten kho: ");
          scanf("%s", kho.TenKho);
          printf("Nhap dia chi kho: ");
          scanf("%s", kho.DiaChi);
          KhoNode *newNode = createKhoNode(kho);
          addTail(&l, &newNode);
          FILE *file = fopen(FilenameKho, "a");
          if (file == NULL) {
            printf("Khong the mo file.\n");
            return;
          }
          fprintf(file, "%s,%s,%s\n", kho.MaKho, kho.TenKho, kho.DiaChi);
          fclose(file);
          printf("Da them kho va luu vao file.\n");
}

void insertNcc(NccList *l, const char *Filenamencc) {
          NhaCC Ncc;
          printf("\nNhap ma nha cung cap: ");
          scanf("%s", Ncc.MaNCC);
          printf("Nhap ten nha cung cap: ");
          scanf("%s", Ncc.TenNCC);
          printf("Nhap dia chi nha cung cap: ");
          scanf("%s", Ncc.diaChi);
          printf("Nhap SDT nha cung cap: ");
          scanf("%s", Ncc.SDT);
          printf("Nhap email nha cung cap: ");
          scanf("%s", Ncc.email);

          NccNode *newNode = createNccNode(Ncc);
          addTail(l, newNode);

          FILE *file = fopen(Filenamencc, "a");
          if (file == NULL) {
            printf("Khong the mo file.\n");
            return;
          }
          fprintf(file, "%s,%s,%s,%s,%s\n", Ncc.MaNCC, Ncc.TenNCC, Ncc.diaChi,
                  Ncc.SDT, Ncc.email);
          fclose(file);
          printf("Da them nha cung cap va luu vao file.\n");
}

void insertKhachHang(KhachHangList *l, const char *Filenamecs) {
          KhachHang Kh;
          printf("\nNhap ma khach hang: ");
          scanf("%s", Kh.kh.ma);
          printf("Nhap ten khach hang: ");
          scanf("%s", Kh.kh.ten);
          printf("Nhap gioi tinh khach hang: ");
          scanf("%s", Kh.gioiTinh);
          printf("Nhap ngay sinh khach hang: ");
          scanf("%d/%d/%d", &Kh.ngaySinh.Ngay, &Kh.ngaySinh.Thang,
                &Kh.ngaySinh.Nam);

          KhachHangNode *newNode = createKhachHangNode(Kh);
          addTail((BikeList *)l, (void *)newNode);

          FILE *file = fopen(Filenamecs, "a");
          if (file == NULL) {
            printf("Khong the mo file.\n");
            return;
          }
          fprintf(file, "%s,%s,%s,%d/%d/%d\n", Kh.kh.ma, Kh.kh.ten, Kh.gioiTinh,
                  Kh.ngaySinh.Ngay, Kh.ngaySinh.Thang, Kh.ngaySinh.Nam);
          fclose(file);
          printf("Da them khach hang va luu vao file.\n");
}

void insertCuaHang(CuaHangList *l, const char *FilenameCuaHang) {
          CuaHang Ch;
          printf("\nNhap ma cua hang: ");
          scanf("%s", Ch.ch.ma);
          printf("Nhap ten cua hang: ");
          scanf("%s", Ch.ch.ten);
          printf("Nhap dia chi cua hang: ");
          scanf("%s", Ch.ch.diaChi);
          printf("Nhap SDT cua hang: ");
          scanf("%s", Ch.ch.SDT);
          printf("Nhap email cua hang: ");
          scanf("%s", Ch.ch.email);

          CuaHangNode *newNode = createCuaHangNode(Ch);
          addTail(l, newNode);

          FILE *file = fopen(FilenameCuaHang, "a");
          if (file == NULL) {
            printf("Khong the mo file.\n");
            return;
          }
          fprintf(file, "%s,%s,%s,%s,%s\n", Ch.ch.ma, Ch.ch.ten, Ch.ch.diaChi,
                  Ch.ch.SDT, Ch.ch.email);
          fclose(file);
          printf("Da them cua hang va luu vao file.\n");
}

void insertNhanVien(NhanVienList *l, const char *FilenameNhanVien) {
          NhanVien Nv;
          printf("\nNhap ma nhan vien: ");
          scanf("%s", Nv.MaNV);
          printf("Nhap ten nhan vien: ");
          scanf("%s", Nv.HoTen);
          printf("Nhap dia chi nhan vien: ");
          scanf("%s", Nv.DiaChi);
          printf("Nhap SDT nhan vien: ");
          scanf("%s", Nv.SoDienThoai);
          printf("Nhap email nhan vien: ");
          scanf("%s", Nv.Email);
          printf("Nhap gioi tinh nhan vien: ");
          scanf("%s", Nv.GioiTinh);
          printf("Nhap ngay sinh nhan vien (dd mm yyyy): ");
          scanf("%d %d %d", &Nv.NgaySinh.Ngay, &Nv.NgaySinh.Thang,
                &Nv.NgaySinh.Nam);

          NhanVienNode *newNode = createNhanVienNode(Nv);
          addTail(l, newNode);

          FILE *file = fopen(FilenameNhanVien, "a");
          if (file == NULL) {
            printf("Khong the mo file.\n");
            return;
          }
          fprintf(file, "%s,%s,%s,%s,%s,%s,%02d/%02d/%d\n", Nv.MaNV, Nv.HoTen,
                  Nv.DiaChi, Nv.SoDienThoai, Nv.Email, Nv.GioiTinh,
                  Nv.NgaySinh.Ngay, Nv.NgaySinh.Thang, Nv.NgaySinh.Nam);
          fclose(file);
          printf("Da them nhan vien va luu vao file.\n");
}

// Hàm cập nhật số lượng trong kho
void updateKho(KhoList *khoList, const char *maXe, int soLuongThayDoi) {
    KhoNode *current = khoList->head;

    // Duyệt qua danh sách kho để tìm xe theo maXe
    while (current != NULL) {
        if (strcmp(current->kho.bike.maXe, maXe) == 0) {
            // Cập nhật số lượng xe trong kho
            current->kho.bike.soLuong += soLuongThayDoi;
            printf("So luong xe '%s' trong kho da duoc cap nhat: %d\n", maXe, current->kho.bike.soLuong);
            return;
        }
        current = current->next;
    }

    // Nếu không tìm thấy xe trong kho
    printf("Khong tim thay xe '%s' trong kho.\n", maXe);
}

void insertHoaDonNhap(HoaDonNhap *l, const char *FilenameHoaDon, KhoList *khoList) {
    HoaDonNhap *hoaDonNhap = (HoaDonNhap *)malloc(sizeof(HoaDonNhap));
    if (hoaDonNhap == NULL) {
        printf("Khong du bo nho de them\n");
        return;
    }

    // Nhập thông tin hóa đơn nhập
    printf("\nNhap ma hoa don: ");
    scanf("%s", hoaDonNhap->hoaDonNhap.maHD);
    printf("Nhap ngay giao dich (dd/mm/yyyy): ");
    scanf("%d/%d/%d", &hoaDonNhap->hoaDonNhap.ngayGiaoDich.Ngay,
                      &hoaDonNhap->hoaDonNhap.ngayGiaoDich.Thang,
                      &hoaDonNhap->hoaDonNhap.ngayGiaoDich.Nam);
    printf("Nhap thanh tien: ");
    scanf("%lf", &hoaDonNhap->hoaDonNhap.thanhTien);
    printf("Nhap ma nha cung cap: ");
    scanf("%s", hoaDonNhap->ncc.MaNCC);
    printf("Nhap ma kho: ");
    scanf("%s", hoaDonNhap->kho.MaKho);
    printf("Nhap ma xe: ");
    scanf("%s", hoaDonNhap->bike.maXe);
    printf("Nhap so luong xe: ");
    scanf("%d", &hoaDonNhap->bike.soLuong);
    printf("Nhap gia nhap: ");
    scanf("%lf", &hoaDonNhap->giaNhap);

    // Cập nhật số lượng xe trong kho
    updateKho(khoList, hoaDonNhap->bike.maXe, hoaDonNhap->bike.soLuong);

    // Lưu thông tin hóa đơn vào file
    FILE *file = fopen(FilenameHoaDon, "a");
    if (file == NULL) {
        printf("Khong the mo file.\n");
        free(hoaDonNhap);
        return;
    }

    fprintf(file, "%s,%02d/%02d/%d,%.2lf,%s,%s,%s,%d,%.2lf\n",
            hoaDonNhap->hoaDonNhap.maHD,
            hoaDonNhap->hoaDonNhap.ngayGiaoDich.Ngay,
            hoaDonNhap->hoaDonNhap.ngayGiaoDich.Thang,
            hoaDonNhap->hoaDonNhap.ngayGiaoDich.Nam,
            hoaDonNhap->hoaDonNhap.thanhTien, hoaDonNhap->ncc.MaNCC,
            hoaDonNhap->kho.MaKho, hoaDonNhap->bike.maXe,
            hoaDonNhap->bike.soLuong, hoaDonNhap->giaNhap);

    fclose(file);
    printf("Da them hoa don nhap va luu vao file.\n");
    free(hoaDonNhap);
}


void insertHoaDonBan(HoaDonBan *l, const char *FilenameHoaDonMua, KhoList *khoList) {
    HoaDonBan *hoaDonBan = (HoaDonBan *)malloc(sizeof(HoaDonBan));
    if (hoaDonBan == NULL) {
        printf("Memory allocation failed!\n");
        return;
    }

    // Nhập thông tin hóa đơn bán
    printf("\nNhap ma hoa don: ");
    scanf("%s", hoaDonBan->hoaDonBan.maHD);
    printf("Nhap ngay giao dich (dd/mm/yyyy): ");
    scanf("%d/%d/%d", &hoaDonBan->hoaDonBan.ngayGiaoDich.Ngay,
                      &hoaDonBan->hoaDonBan.ngayGiaoDich.Thang,
                      &hoaDonBan->hoaDonBan.ngayGiaoDich.Nam);
    printf("Nhap ma khach hang: ");
    scanf("%s", hoaDonBan->kh.kh.ma);
    printf("Nhap ma xe: ");
    scanf("%s", hoaDonBan->bike.maXe);
    printf("Nhap so luong xe: ");
    scanf("%d", &hoaDonBan->soLuongBan);
    printf("Nhap don gia: ");
    scanf("%lf", &hoaDonBan->donGia);

    // Cập nhật số lượng xe trong kho (giảm số lượng khi bán)
    updateKho(khoList, hoaDonBan->bike.maXe, -hoaDonBan->soLuongBan);

    // Lưu thông tin hóa đơn bán vào file
    FILE *file = fopen(FilenameHoaDonMua, "a");
    if (file == NULL) {
        printf("Khong the mo file.\n");
        free(hoaDonBan);
        return;
    }

    fprintf(file, "%s,%02d/%02d/%d,%s,%s,%d,%.2lf\n",
            hoaDonBan->hoaDonBan.maHD,
            hoaDonBan->hoaDonBan.ngayGiaoDich.Ngay,
            hoaDonBan->hoaDonBan.ngayGiaoDich.Thang,
            hoaDonBan->hoaDonBan.ngayGiaoDich.Nam, hoaDonBan->kh.kh.ma,
            hoaDonBan->bike.maXe, hoaDonBan->soLuongBan, hoaDonBan->donGia);

    fclose(file);
    printf("Da them hoa don ban va luu vao file.\n");
    free(hoaDonBan);
}

void selectThongKe(const char *FilenameThongKe, const char *maHD) {
    FILE *file = fopen(FilenameThongKe, "r");
    if (file == NULL) {
        printf("Khong the mo file.\n");
        return;
    }

    ThongKe thongKe;
    int found = 0;

    while (fscanf(file, "%s,%d/%d/%d,%d,%d,%.2lf,%.2lf\n", thongKe.hoaDon.maHD,
                  &thongKe.hoaDon.ngayGiaoDich.Ngay, &thongKe.hoaDon.ngayGiaoDich.Thang,
                  &thongKe.hoaDon.ngayGiaoDich.Nam, &thongKe.tongSoLuongBan,
                  &thongKe.hoaDonBan.Tongtienban, &thongKe.tongTienNhap, &thongKe.tongTienBan) != EOF) {
        if (strcmp(thongKe.hoaDon.maHD, maHD) == 0) {
            found = 1;
            printf("Thong ke cho Hoa Don %s:\n", thongKe.hoaDon.maHD);
            printf("Ngay: %02d/%02d/%d\n", thongKe.hoaDon.ngayGiaoDich.Ngay,
                    thongKe.hoaDon.ngayGiaoDich.Thang, thongKe.hoaDon.ngayGiaoDich.Nam);

            // Hiển thị số lượng xe nhập và bán theo maXe trong HoaDonNhap và HoaDonBan
            printf("Xe nhap (maXe: %s) - So luong: %d\n", thongKe.hoaDonNhap.bike.maXe, thongKe.hoaDonNhap.soLuongNhap);
            printf("Xe ban (maXe: %s) - So luong: %d\n", thongKe.hoaDonBan.bike.maXe, thongKe.hoaDonBan.soLuongBan);
            printf("Tong tien nhap: %.2lf, Tong tien ban: %.2lf\n", thongKe.tongTienNhap, thongKe.tongTienBan);
        }
    }

    if (!found) {
        printf("Khong tim thay hoa don voi maHD: %s\n", maHD);
    }

    fclose(file);
}


void insertThongKe(ThongKe *l, const char *FilenameThongKe) {
    ThongKe *thongKe = (ThongKe *)malloc(sizeof(ThongKe));
    if (thongKe == NULL) {
        printf("Memory allocation failed!\n");
        return;
    }

    printf("\nNhap ma hoa don: ");
    scanf("%s", thongKe->hoaDon.maHD);
    printf("Nhap ngay giao dich (dd/mm/yyyy): ");
    scanf("%d/%d/%d", &thongKe->hoaDon.ngayGiaoDich.Ngay,
                      &thongKe->hoaDon.ngayGiaoDich.Thang,
                      &thongKe->hoaDon.ngayGiaoDich.Nam);

    // Nhập thông tin cho HoaDonNhap
    printf("Nhap gia nhap xe: ");
    scanf("%lf", &thongKe->hoaDonNhap.giaNhap);

    printf("Nhap so luong xe nhap: ");
    scanf("%d", &thongKe->hoaDonNhap.soLuongNhap);  // Nhập soLuong xe trong HoaDonNhap
  
    // Tính tổng tiền nhập
    double tongTienNhap = thongKe->hoaDonNhap.giaNhap * thongKe->hoaDonNhap.bike.soLuong;

    // Nhập thông tin cho ThongKe
    printf("Nhap tong so luong xe ban: ");
    scanf("%d", &thongKe->tongSoLuongBan);  // Nhập tongSoLuongBan cho ThongKe
    printf("Nhap tong tien ban: ");
    scanf("%lf", &thongKe->tongTienBan);  // Nhập tongTienBan cho ThongKe

    // Ghi thông tin vào file
    FILE *file = fopen(FilenameThongKe, "a");
    if (file == NULL) {
        printf("Khong the mo file.\n");
        free(thongKe);
        return;
    }

    // Ghi thông tin vào file (thêm tổng tiền nhập vào báo cáo)
    fprintf(file, "%s,%02d/%02d/%d,%d,%d,%.2lf,%.2lf\n",
            thongKe->hoaDon.maHD, thongKe->hoaDon.ngayGiaoDich.Ngay,
            thongKe->hoaDon.ngayGiaoDich.Thang,
            thongKe->hoaDon.ngayGiaoDich.Nam, thongKe->tongSoLuongBan,
            thongKe->, tongTienNhap, thongKe->tongTienBan);

    fclose(file);

    printf("Da them thong ke va luu vao file.\n");
    free(thongKe);
}



// Function display

// Xe

void displayBikeHeaders() {
          printf("\n%-10s | %-20s | %-10s | %-15s | %-15s | %-10s\n", "Ma Xe",
                 "Ten Xe", "So Luong", "Mau Sac", "Tinh Trang", "Don Gia");
          printf("-------------------------------------------------------------"
                 "--------"
                 "----------------------\n");
}

void displayBike(Bike bike) {
          printf("%-10s | %-20s | %-10d | %-15s | %-15d | %-10.2f\n", bike.maXe,
                 bike.tenXe, bike.soLuong, bike.mauSac, bike.tinhTrang,
                 bike.donGia);
}

// Kho

void displayKhoHeaders() {
          printf("\n%-10s | %-20s | %-30s\n", "Ma Kho", "Ten Kho", "Dia Chi");
          printf(
              "------------------------------------------------------------\n");
}

void displayKho(Kho kho) {
          printf("%-10s | %-20s | %-30s\n", kho.maKho, kho.tenKho, kho.diaChi);
}

// Nha Cung Cap

void displayNccHeaders() {
          printf("\n%-10s | %-30s | %-30s | %-15s | %-30s\n", "Ma NCC",
                 "Ten NCC", "Dia Chi", "SDT", "Email");
          printf("-------------------------------------------------------------"
                 "--------"
                 "----------\n");
}

void displayNcc(NhaCC ncc) {
          printf("%-10s | %-30s | %-30s | %-15s | %-30s\n", ncc.MaNCC,
                 ncc.TenNCC, ncc.diaChi, ncc.SDT, ncc.email);
}

// Cua Hang

void displayCuaHangHeaders() {
          printf("\n%-10s | %-30s | %-30s | %-15s | %-30s\n", "Ma CH", "Ten CH",
                 "Dia Chi", "SDT", "Email");
          printf("-------------------------------------------------------------"
                 "--------"
                 "----------\n");
}

void displayCuaHang(CuaHang ch) {
          printf("%-10s | %-30s | %-30s | %-15s | %-30s\n", ch.ch.ma, ch.ch.ten,
                 ch.ch.diaChi, ch.ch.SDT, ch.ch.email);
}

// Nhan Vien

void displayNhanVienHeaders() {
          printf("\n%-10s | %-20s | %-30s | %-15s | %-30s | %-10s | %-10s\n",
                 "Ma NV", "Ten NV", "Dia Chi", "SDT", "Email", "Gioi Tinh",
                 "Ngay Sinh");
          printf("-------------------------------------------------------------"
                 "--------"
                 "------------------------------\n");
}

void displayNhanVien(NhanVien nv) {
          printf(
              "%-10s | %-20s | %-30s | %-15s | %-30s | %-10s | %02d/%02d/%d\n",
              nv.nv.ma, nv.nv.ten, nv.nv.diaChi, nv.nv.SDT, nv.nv.email,
              nv.gioiTinh, nv.ngaySinh.Ngay, nv.ngaySinh.Thang,
              nv.ngaySinh.Nam);
}

// Khach Hang

void displayKhachHangHeaders() {
          printf("\n%-10s | %-20s | %-30s | %-15s | %-30s | %-10s | %-10s | "
                 "%-10s\n",
                 "Ma KH", "Ten KH", "Dia Chi", "SDT", "Email", "Gioi Tinh",
                 "Ngay Sinh", "Ngay Mua");
          printf("-------------------------------------------------------------"
                 "--------"
                 "-------------------------------------------\n");
}

void displayKhachHang(KhachHang Kh) {
          printf(
              "%-10s | %-20s | %-30s | %-15s | %-3s | %-10s | %02d/%02d/%d | "
              "%02d/%02d/%d\n",
              Kh.kh.ma, Kh.kh.ten, Kh.kh.diaChi, Kh.kh.SDT, Kh.kh.email,
              Kh.gioiTinh, Kh.ngaySinh.Ngay, Kh.ngaySinh.Thang, Kh.ngaySinh.Nam,
              Kh.ngayMua.Ngay, Kh.ngayMua.Thang, Kh.ngayMua.Nam);
}

// Hoa Don

void displayHoaDonNhapHeaders() {
          printf("\n%-10s | %-20s | %-30s | %-15s | %-30s | %-10s | %-10s | "
                 "%-10s\n",
                 "Ma HD", "Ma NCC", "Ma Kho", "Ma Xe", "So Luong", "Gia Nhap",
                 "Tong Tien", "Ngay Giao Dich");
          printf("-------------------------------------------------------------"
                 "--------"
                 "-------------------------------------------\n");
}

void displayHoaDonNhap(HoaDonNhap hoaDonNhap) {
          printf(
              "%-10s | %-20s | %-30s | %-15s | %-30.2f | %-10.2f | %-10.2f | "
              "%02d/%02d/%d\n",
              hoaDonNhap.hoaDonNhap.maHD, hoaDonNhap.ncc.MaNCC,
              hoaDonNhap.kho.maKho, hoaDonNhap.bike.maXe,
              hoaDonNhap.bike.donGia, hoaDonNhap.giaNhap,
              hoaDonNhap.hoaDonNhap.thanhTien,
              hoaDonNhap.hoaDonNhap.ngayGiaoDich.Ngay,
              hoaDonNhap.hoaDonNhap.ngayGiaoDich.Thang,
              hoaDonNhap.hoaDonNhap.ngayGiaoDich.Nam);
}

void displayHoaDonBanHeaders() {}

// Applicable function

// Khai bao ham ghi du lieu danh sach Nhan vien vao file
void WriteNhanVienToFile(NhanVienList *pHead, const char *Filename) {
  FILE *fp = fopen(Filename, "w");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return;
  }
  NhanVienList *pTemp = pHead;
  while (pTemp != NULL) {
    fprintf(fp, "%s,%s,%s,%s,%s,%s,%s,%.2f\n", pTemp->NV.MaNV, pTemp->NV.HoTen,
            pTemp->NV.NgaySinh, pTemp->NV.GioiTinh, pTemp->NV.DiaChi,
            pTemp->NV.SoDienThoai, pTemp->NV.ChucVu, pTemp->NV.LuongCoBan);
    pTemp = pTemp->pNext;
  }
  fclose(fp);
}
// Khai bao ham ghi du lieu danh sach Kho vao file
void WriteKhoToFile(KhoList *pHead, const char *Filename) {
  FILE *fp = fopen(Filename, "w");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return;
  }
  KhoList *pTemp = pHead;
  while (pTemp != NULL) {
    fprintf(fp, "%s,%s,%s,%s\n", pTemp->K.MaKho, pTemp->K.TenKho,
            pTemp->K.DiaChi, pTemp->K.SoDienThoai);
    pTemp = pTemp->pNext;
  }
  fclose(fp);
}
// Khai bao ham ghi du lieu danh sach NCC vao file
void WriteNCCToFile(NCCList *pHead, const char *Filename) {
  FILE *fp = fopen(Filename, "w");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return;
  }
  NCCList *pTemp = pHead;
  while (pTemp != NULL) {
    fprintf(fp, "%s,%s,%s,%s\n", pTemp->N.MaNCC, pTemp->N.TenNCC,
            pTemp->N.DiaChi, pTemp->N.SoDienThoai);
    pTemp = pTemp->pNext;
  }
  fclose(fp);
}
// Khai bao ham ghi du lieu danh sach Thong ke vao file
void WriteTkToFile(TkList *pHead, const char *Filename) {
  FILE *fp = fopen(Filename, "w");
  if (fp == NULL) {
    printf("Khong mo duoc file!");
    return;
  }
  TkList *pTemp = pHead;
  while (pTemp != NULL) {
    fprintf(fp, "%s,%s,%s,%d,%.2f\n", pTemp->T.MaNV, pTemp->T.TenNV,
            pTemp->T.ChucVu, pTemp->T.SoLuongBanHang, pTemp->T.TongDoanhThu);
    pTemp = pTemp->pNext;
  }
  fclose(fp);
}
// Khai bao ham xuat du lieu danh sach Nhan vien
void PrintNhanVienList(NhanVienList *pHead) {
  if (pHead == NULL) {
    printf("Danh sach rong!\n");
    return;
  }
  NhanVienList *pTemp = pHead;
  printf("%-10s%-50s%-11s%-4s%-100s%-15s%-30s%-10s\n", "MaNV", "HoTen",
         "NgaySinh", "GT", "DiaChi", "SoDienThoai", "ChucVu", "LuongCoBan");
  while (pTemp != NULL) {
    printf("%-10s%-50s%-11s%-4s%-100s%-15s%-30s%-10.2f\n", pTemp->NV.MaNV,
           pTemp->NV.HoTen, pTemp->NV.NgaySinh, pTemp->NV.GioiTinh,
           pTemp->NV.DiaChi, pTemp->NV.SoDienThoai, pTemp->NV.ChucVu,
           pTemp->NV.LuongCoBan);
    pTemp = pTemp->pNext;
  }
}
// Khai bao ham xuat du lieu danh sach Kho
void PrintKhoList(KhoList *pHead) {
  if (pHead == NULL) {
    printf("Danh sach rong!\n");
    return;
  }
  KhoList *pTemp = pHead;
  printf("%-10s%-50s%-100s%-15s\n", "MaKho", "TenKho", "DiaChi", "SoDienThoai");
  while (pTemp != NULL) {
    printf("%-10s%-50s%-100s%-15s\n", pTemp->K.MaKho, pTemp->K.TenKho,
           pTemp->K.DiaChi, pTemp->K.SoDienThoai);
    pTemp = pTemp->pNext;
  }
}
// Khai bao ham xuat du lieu danh sach NCC
void PrintNCCList(NCCList *pHead) {
  if (pHead == NULL) {
    printf("Danh sach rong!\n");
    return;
  }
  NCCList *pTemp = pHead;
  printf("%-10s%-50s%-100s%-15s\n", "MaNCC", "TenNCC", "DiaChi", "SoDienThoai");
  while (pTemp != NULL) {
    printf("%-10s%-50s%-100s%-15s\n", pTemp->N.MaNCC, pTemp->N.TenNCC,
           pTemp->N.DiaChi, pTemp->N.SoDienThoai);
    pTemp = pTemp->pNext;
  }
}
// Khai bao ham xuat du lieu danh sach Thong ke
void PrintTkList(TkList *pHead) {
  if (pHead == NULL) {
    printf("Danh sach rong!\n");
    return;
  }
  TkList *pTemp = pHead;
  printf("%-10s%-50s%-30s%-15s%-15s\n", "MaNV", "TenNV", "ChucVu",
         "SoLuongBanHang", "TongDoanhThu");
  while (pTemp != NULL) {
    printf("%-10s%-50s%-30s%-15d%-15.2f\n", pTemp->T.MaNV, pTemp->T.TenNV,
           pTemp->T.ChucVu, pTemp->T.SoLuongBanHang, pTemp->T.TongDoanhThu);
    pTemp = pTemp->pNext;
  }
}
// Khai bao ham tim kiem Nhan vien theo MaNV
NhanVienList *SearchNhanVien(NhanVienList *pHead, const char *MaNV) {
  if (pHead == NULL) {
    return NULL;
  }
  NhanVienList *pTemp = pHead;
  while (pTemp != NULL) {
    if (strcmp(pTemp->NV.MaNV, MaNV) == 0) {
      return pTemp;
    }
    pTemp = pTemp->pNext;
  }
  return NULL;
}
// Khai bao ham tim kiem Kho theo MaKho
KhoList *SearchKho(KhoList *pHead, const char *MaKho) {
  if (pHead == NULL) {
    return NULL;
  }
  KhoList *pTemp = pHead;
  while (pTemp != NULL) {
    if (strcmp(pTemp->K.MaKho, MaKho) == 0) {
      return pTemp;
    }
    pTemp = pTemp->pNext;
  }
  return NULL;
}
// Khai bao ham tim kiem NCC theo MaNCC
NCCList *SearchNCC(NCCList *pHead, const char *MaNCC) {
  if (pHead == NULL) {
    return NULL;
  }
  NCCList *pTemp = pHead;
  while (pTemp != NULL) {
    if (strcmp(pTemp->N.MaNCC, MaNCC) == 0) {
      return pTemp;
    }
    pTemp = pTemp->pNext;
  }
  return NULL;
}
// Khai bao ham tim kiem Thong ke theo MaNV
TkList *SearchTk(TkList *pHead, const char *MaNV) {
  if (pHead == NULL) {
    return NULL;
  }
  TkList *pTemp = pHead;
  while (pTemp != NULL) {
    if (strcmp(pTemp->T.MaNV, MaNV) == 0) {
      return pTemp;
    }
    pTemp = pTemp->pNext;
  }
  return NULL;
}
// Khai bao ham xoa Nhan vien theo MaNV
NhanVienList *DeleteNhanVien(NhanVienList *pHead, const char *MaNV) {
  if (pHead == NULL) {
    return NULL;
  }
  NhanVienList *pTemp = pHead;
  NhanVienList *pPre = NULL;
  while (pTemp != NULL) {
    if (strcmp(pTemp->NV.MaNV, MaNV) == 0) {
      if (pPre == NULL) {
        pHead = pTemp->pNext;
      } else {
        pPre->pNext = pTemp->pNext;
      }
      free(pTemp);
      return pHead;
    }
    pPre = pTemp;
    pTemp = pTemp->pNext;
  }
  return pHead;
}
// Khai bao ham xoa Kho theo MaKho
KhoList *DeleteKho(KhoList *pHead, const char *MaKho) {
  if (pHead == NULL) {
    return NULL;
  }
  KhoList *pTemp = pHead;
  KhoList *pPre = NULL;
  while (pTemp != NULL) {
    if (strcmp(pTemp->K.MaKho, MaKho) == 0) {
      if (pPre == NULL) {
        pHead = pTemp->pNext;
      } else {
        pPre->pNext = pTemp->pNext;
      }
      free(pTemp);
      return pHead;
    }
    pPre = pTemp;
    pTemp = pTemp->pNext;
  }
  return pHead;
}
// Khai bao ham xoa NCC theo MaNCC
NCCList *DeleteNCC(NCCList *pHead, const char *MaNCC) {
  if (pHead == NULL) {
    return NULL;
  }
  NCCList *pTemp = pHead;
  NCCList *pPre = NULL;
  while (pTemp != NULL) {
    if (strcmp(pTemp->N.MaNCC, MaNCC) == 0) {
      if (pPre == NULL) {
        pHead = pTemp->pNext;
      } else {
        pPre->pNext = pTemp->pNext;
      }
      free(pTemp);
      return pHead;
    }
    pPre = pTemp;
    pTemp = pTemp->pNext;
  }
  return pHead;
}
// Khai bao ham xoa Thong ke theo MaNV
TkList *DeleteTk(TkList *pHead, const char *MaNV) {
  if (pHead == NULL) {
    return NULL;
  }
  TkList *pTemp = pHead;
  TkList *pPre = NULL;
  while (pTemp != NULL) {
    if (strcmp(pTemp->T.MaNV, MaNV) == 0) {
      if (pPre == NULL) {
        pHead = pTemp->pNext;
      } else {
        pPre->pNext = pTemp->pNext;
      }
      free(pTemp);
      return pHead;
    }
    pPre = pTemp;
    pTemp = pTemp->pNext;
  }
  return pHead;
}
// Khai bao ham sua thong tin Nhan vien
void EditNhanVien(NhanVienList *pHead, const char *MaNV) {
  NhanVienList *pTemp = SearchNhanVien(pHead, MaNV);
  if (pTemp == NULL) {
    printf("Khong tim thay Nhan vien!\n");
    return;
  }
  printf("Nhap thong tin Nhan vien moi:\n");
  printf("HoTen: ");
  fflush(stdin);
  fgets(pTemp->NV.HoTen, sizeof(pTemp->NV.HoTen), stdin);
  printf("NgaySinh: ");
  fflush(stdin);
  fgets(pTemp->NV.NgaySinh, sizeof(pTemp->NV.NgaySinh), stdin);
  printf("GioiTinh: ");
  fflush(stdin);
  fgets(pTemp->NV.GioiTinh, sizeof(pTemp->NV.GioiTinh), stdin);
  printf("DiaChi: ");
  fflush(stdin);
  fgets(pTemp->NV.DiaChi, sizeof(pTemp->NV.DiaChi), stdin);
  printf("SoDienThoai: ");
  fflush(stdin);
  fgets(pTemp->NV.SoDienThoai, sizeof(pTemp->NV.SoDienThoai), stdin);
  printf("ChucVu: ");
  fflush(stdin);
  fgets(pTemp->NV.ChucVu, sizeof(pTemp->NV.ChucVu), stdin);
  printf("LuongCoBan: ");
  scanf("%f", &pTemp->NV.LuongCoBan);
}
// Khai bao ham sua thong tin Kho
void EditKho(KhoList *pHead, const char *MaKho) {
  KhoList *pTemp = SearchKho(pHead, MaKho);
  if (pTemp == NULL) {
    printf("Khong tim thay Kho!\n");
    return;
  }
  printf("Nhap thong tin Kho moi:\n");
  printf("TenKho: ");
  fflush(stdin);
  fgets(pTemp->K.TenKho, sizeof(pTemp->K.TenKho), stdin);
  printf("DiaChi: ");
  fflush(stdin);
  fgets(pTemp->K.DiaChi, sizeof(pTemp->K.DiaChi), stdin);
  printf("SoDienThoai: ");
  fflush(stdin);
  fgets(pTemp->K.SoDienThoai, sizeof(pTemp->K.SoDienThoai), stdin);
}

// Khai bao ham sua thong tin NCC

void EditNCC(NCCList *pHead, const char *MaNCC) {
  NCCList *pTemp = SearchNCC(pHead, MaNCC);
  if (pTemp == NULL) {
    printf("Khong tim thay NCC!\n");
    return;
  }
  printf("Nhap thong tin NCC moi:\n");
  printf("TenNCC: ");
  fflush(stdin);
  fgets(pTemp->N.TenNCC, sizeof(pTemp->N.TenNCC), stdin);
  printf("DiaChi: ");
  fflush(stdin);
  fgets(pTemp->N.DiaChi, sizeof(pTemp->N.DiaChi), stdin);
  printf("SoDienThoai: ");
  fflush(stdin);
  fgets(pTemp->N.SoDienThoai, sizeof(pTemp->N.SoDienThoai), stdin);
}

// Khai bao ham sua thong tin Thong ke

void EditTk(TkList *pHead, const char *MaNV) {
  TkList *pTemp = SearchTk(pHead, MaNV);
  if (pTemp == NULL) {
    printf("Khong tim thay Thong ke!\n");
    return;
  }
  printf("Nhap thong tin Thong ke moi:\n");
  printf("TenNV: ");
  fflush(stdin);
  fgets(pTemp->T.TenNV, sizeof(pTemp->T.TenNV), stdin);
  printf("ChucVu: ");
  fflush(stdin);
  fgets(pTemp->T.ChucVu, sizeof(pTemp->T.ChucVu), stdin);
  printf("SoLuongBanHang: ");
  scanf("%d", &pTemp->T.SoLuongBanHang);
  printf("TongDoanhThu: ");
  scanf("%f", &pTemp->T.TongDoanhThu);
}
// Khai bao ham them Nhan vien moi
void AddNewNhanVien(NhanVienList *pHead, const char *Filenamenv) {
  NhanVien NV;
  printf("Nhap thong tin Nhan vien moi:\n");
  printf("MaNV: ");
  fflush(stdin);
  fgets(NV.MaNV, sizeof(NV.MaNV), stdin);
  printf("HoTen: ");
  fflush(stdin);
  fgets(NV.HoTen, sizeof(NV.HoTen), stdin);
  printf("NgaySinh: ");
  fflush(stdin);
  fgets(NV.NgaySinh, sizeof(NV.NgaySinh), stdin);
  printf("GioiTinh: ");
  fflush(stdin);
  fgets(NV.GioiTinh, sizeof(NV.GioiTinh), stdin);
  printf("DiaChi: ");
  fflush(stdin);
  fgets(NV.DiaChi, sizeof(NV.DiaChi), stdin);
  printf("SoDienThoai: ");
  fflush(stdin);
  fgets(NV.SoDienThoai, sizeof(NV.SoDienThoai), stdin);
  printf("ChucVu: ");
  fflush(stdin);
  fgets(NV.ChucVu, sizeof(NV.ChucVu), stdin);
  printf("LuongCoBan: ");
  scanf("%f", &NV.LuongCoBan);
  pHead = AddNhanVien(pHead, NV);
  WriteNhanVienToFile(pHead, Filenamenv);
  printf("Them Nhan vien thanh cong!\n");
}
// Khai bao ham them Kho moi
void AddNewKho(KhoList *pHead, const char *Filenamekho) {
  Kho K;
  printf("Nhap thong tin Kho moi:\n");
  printf("MaKho: ");
  fflush(stdin);
  fgets(K.MaKho, sizeof(K.MaKho), stdin);
  printf("TenKho: ");
  fflush(stdin);
  fgets(K.TenKho, sizeof(K.TenKho), stdin);
  printf("DiaChi: ");
  fflush(stdin);
  fgets(K.DiaChi, sizeof(K.DiaChi), stdin);
  printf("SoDienThoai: ");
  fflush(stdin);
  fgets(K.SoDienThoai, sizeof(K.SoDienThoai), stdin);
  pHead = AddKho(pHead, K);
  WriteKhoToFile(pHead, Filenamekho);
  printf("Them Kho thanh cong!\n");
}
// Khai bao ham them NCC moi
void AddNewNCC(NCCList *pHead, const char *Filenamencc) {
  NCC N;
  printf("Nhap thong tin NCC moi:\n");
  printf("MaNCC: ");
  fflush(stdin);
  fgets(N.MaNCC, sizeof(N.MaNCC), stdin);
  printf("TenNCC: ");
  fflush(stdin);
  fgets(N.TenNCC, sizeof(N.TenNCC), stdin);
  printf("DiaChi: ");
  fflush(stdin);
  fgets(N.DiaChi, sizeof(N.DiaChi), stdin);
  printf("SoDienThoai: ");
  fflush(stdin);
  fgets(N.SoDienThoai, sizeof(N.DiaChi), stdin);
  pHead = AddNCC(pHead, N);
  WriteNCCToFile(pHead, Filenamencc);
  printf("Them NCC thanh cong!\n");
}
// Khai bao ham them Thong ke moi
void AddNewTk(TkList *pHead, const char *Filenametk) {
  ThongKe T;
  printf("Nhap thong tin Thong ke moi:\n");
  printf("MaNV: ");
  fflush(stdin);
  fgets(T.MaNV, sizeof(T.MaNV), stdin);
  printf("TenNV: ");
  fflush(stdin);
  fgets(T.TenNV, sizeof(T.TenNV), stdin);
  printf("ChucVu: ");
  fflush(stdin);
  fgets(T.ChucVu, sizeof(T.ChucVu), stdin);
  printf("SoLuongBanHang: ");
  scanf("%d", &T.SoLuongBanHang);
  printf("TongDoanhThu: ");
  scanf("%f", &T.TongDoanhThu);
  pHead = AddTk(pHead, T);
  WriteTkToFile(pHead, Filenametk);
  printf("Them Thong ke thanh cong!\n");
}
// Khai bao ham menu Nhan vien
void menuNhanVien(NhanVienList *nvhead, const char *Filenamenv) {
  int choice;
  while (1) {
    printf("\n===== MENU QUAN LY NHAN VIEN =====\n");
    printf("1. Hien thi danh sach Nhan vien\n");
    printf("2. Them Nhan vien moi\n");
    printf("3. Tim kiem Nhan vien\n");
    printf("4. Xoa Nhan vien\n");
    printf("5. Sua thong tin Nhan vien\n");
    printf("0. Quay lai menu chinh\n");
    printf("Lua chon cua ban: ");
    scanf("%d", &choice);
    switch (choice) {
    case 1:
      PrintNhanVienList(nvhead);
      break;
    case 2:
      AddNewNhanVien(nvhead, Filenamenv);
      break;
    case 3: {
      char MaNV[10];
      printf("Nhap MaNV can tim kiem: ");
      fflush(stdin);
      fgets(MaNV, sizeof(MaNV), stdin);
      NhanVienList *pTemp = SearchNhanVien(nvhead, MaNV);
      if (pTemp == NULL) {
        printf("Khong tim thay Nhan vien!\n");
      } else {
        printf("%-10s%-50s%-11s%-4s%-100s%-15s%-30s%-10s\n", "MaNV", "HoTen",
               "NgaySinh", "GT", "DiaChi", "SoDienThoai", "ChucVu",
               "LuongCoBan");
        printf("%-10s%-50s%-11s%-4s%-100s%-15s%-30s%-10.2f\n", pTemp->NV.MaNV,
               pTemp->NV.HoTen, pTemp->NV.NgaySinh, pTemp->NV.GioiTinh,
               pTemp->NV.DiaChi, pTemp->NV.SoDienThoai, pTemp->NV.ChucVu,
               pTemp->NV.LuongCoBan);
      }
      break;
    }
    case 4: {
      char MaNV[10];
      printf("Nhap MaNV can xoa: ");
      fflush(stdin);
      fgets(MaNV, sizeof(MaNV), stdin);
      nvhead = DeleteNhanVien(nvhead, MaNV);
      WriteNhanVienToFile(nvhead, Filenamenv);
      printf("Xoa Nhan vien thanh cong!\n");
      break;
    }
    case 5: {
      char MaNV[10];
      printf("Nhap MaNV can sua: ");
      fflush(stdin);
      fgets(MaNV, sizeof(MaNV), stdin);
      EditNhanVien(nvhead, MaNV);
      WriteNhanVienToFile(nvhead, Filenamenv);
      printf("Sua thong tin Nhan vien thanh cong!\n");
      break;
    }
    case 0:
      return;
    default:
      printf("Lua chon khong hop le!\n");
    }
  }
}
// Khai bao ham menu Kho
void menuKho(KhoList *kho, const char *FilenameKho) {
  int choice;
  while (1) {
    printf("\n===== MENU QUAN LY KHO =====\n");
    printf("1. Hien thi danh sach Kho\n");
    printf("2. Them Kho moi\n");
    printf("3. Tim kiem Kho\n");
    printf("4. Xoa Kho\n");
    printf("5. Sua thong tin Kho\n");
    printf("0. Quay lai menu chinh\n");
    printf("Lua chon cua ban: ");
    scanf("%d", &choice);
    switch (choice) {
    case 1:
      PrintKhoList(kho);
      break;
    case 2:
      AddNewKho(kho, FilenameKho);
      break;
    case 3: {
      char MaKho[10];
      printf("Nhap MaKho can tim kiem: ");
      fflush(stdin);
      fgets(MaKho, sizeof(MaKho), stdin);
      KhoList *pTemp = SearchKho(kho, MaKho);
      if (pTemp == NULL) {
        printf("Khong tim thay Kho!\n");
      } else {
        printf("%-10s%-50s%-100s%-15s\n", "MaKho", "TenKho", "DiaChi",
               "SoDienThoai");
        printf("%-10s%-50s%-100s%-15s\n", pTemp->K.MaKho, pTemp->K.TenKho,
               pTemp->K.DiaChi, pTemp->K.SoDienThoai);
      }
      break;
    }
    case 4: {
      char MaKho[10];
      printf("Nhap MaKho can xoa: ");
      fflush(stdin);
      fgets(MaKho, sizeof(MaKho), stdin);
      kho = DeleteKho(kho, MaKho);
      WriteKhoToFile(kho, FilenameKho);
      printf("Xoa Kho thanh cong!\n");
      break;
    }
    case 5: {
      char MaKho[10];
      printf("Nhap MaKho can sua: ");
      fflush(stdin);
      fgets(MaKho, sizeof(MaKho), stdin);
      EditKho(kho, MaKho);
      WriteKhoToFile(kho, FilenameKho);
      printf("Sua thong tin Kho thanh cong!\n");
      break;
    }
    case 0:
      return;
    default:
      printf("Lua chon khong hop le!\n");
    }
  }
}
// Khai bao ham menu NCC
void menuNcc(NCCList *ncchead, const char *Filenamencc) {
  int choice;
  while (1) {
    printf("\n===== MENU QUAN LY NCC =====\n");
    printf("1. Hien thi danh sach NCC\n");
    printf("2. Them NCC moi\n");
    printf("3. Tim kiem NCC\n");
    printf("4. Xoa NCC\n");
    printf("5. Sua thong tin NCC\n");
    printf("0. Quay lai menu chinh\n");
    printf("Lua chon cua ban: ");
    scanf("%d", &choice);
    switch (choice) {
    case 1:
      PrintNCCList(ncchead);
      break;
    case 2:
      AddNewNCC(ncchead, Filenamencc);
      break;
    case 3: {
      char MaNCC[10];
      printf("Nhap MaNCC can tim kiem: ");
      fflush(stdin);
      fgets(MaNCC,sizeof(MaNCC) ,stdin);
      NCCList *pTemp = SearchNCC(ncchead, MaNCC);
      if (pTemp == NULL) {
        printf("Khong tim thay NCC!\n");
      } else {
        printf("%-10s%-50s%-100s%-15s\n", "MaNCC", "TenNCC", "DiaChi",
               "SoDienThoai");
      }

// menuXe

void suaThongTinXe(BikeList *bike, const char *FilenameBike) {
          char maXeCanSua[10];
          Bike bikeCanSua;
          printf("\nNhap ma xe can sua: ");
          scanf("%s", maXeCanSua);
          BikeNode *current = bike->head;
          while (current != NULL) {
            if (strcmp(current->bike.maXe, maXeCanSua) == 0) {
              printf("\nNhap ten xe: ");
              scanf("%s", bikeCanSua.tenXe);
              printf("Nhap so luong xe: ");
              scanf("%d", &bikeCanSua.soLuong);
              printf("Nhap mau sac xe: ");
              scanf("%s", bikeCanSua.mauSac);
              printf("Nhap tinh trang xe (1: Moi, 0: Cu): ");
              scanf("%d", &bikeCanSua.tinhTrang);
              printf("Nhap don gia: ");
              scanf("%f", &bikeCanSua.donGia);
              strcpy(current->bike.tenXe, bikeCanSua.tenXe);
              current->bike.soLuong = bikeCanSua.soLuong;
              strcpy(current->bike.mauSac, bikeCanSua.mauSac);
              current->bike.tinhTrang = bikeCanSua.tinhTrang;
              current->bike.donGia = bikeCanSua.donGia;
              FILE *file = fopen(FilenameBike, "w");
              if (file == NULL) {
                printf("Khong the mo file.\n");
                return;
              }
              BikeNode *temp = bike->head;
              while (temp != NULL) {
                fprintf(file, "%s,%s,%d,%s,%d,%.2f\n", temp->bike.maXe,
                        temp->bike.tenXe, temp->bike.soLuong, temp->bike.mauSac,
                        temp->bike.tinhTrang, temp->bike.donGia);
                temp = temp->next;
              }
              fclose(file);
              printf("Da cap nhat thong tin xe.\n");
              return;
            } else {
              current = current->next;
            }
          }
          if (current == NULL) {
            printf("Khong tim thay xe co ma %s.\n", maXeCanSua);
          }
}

void deleteBike(BikeList *bike, const char *FilenameBike) {
          char maXeCanXoa[10];
          printf("\nNhap ma xe can xoa: ");
          scanf("%s", maXeCanXoa);

          BikeNode *current = bike->head;
          BikeNode *prev = NULL;

          while (current != NULL) {
            if (strcmp(current->bike.maXe, maXeCanXoa) == 0) {
              if (prev == NULL) {
                bike->head = current->next;
              } else {
                prev->next = current->next;
              }
              free(current);

              FILE *file = fopen(FilenameBike, "w");
              if (file == NULL) {
                printf("Khong the mo file.\n");
                return;
              }
              BikeNode *temp = bike->head;
              while (temp != NULL) {
                fprintf(file, "%s,%s,%d,%s,%d,%.2f\n", temp->bike.maXe,
                        temp->bike.tenXe, temp->bike.soLuong, temp->bike.mauSac,
                        temp->bike.tinhTrang, temp->bike.donGia);
                temp = temp->next;
              }
              fclose(file);

              printf("Da xoa xe co ma %s.\n", maXeCanXoa);
              return;
            } else {
              prev = current;
              current = current->next;
            }
          }

          if (current == NULL) {
            printf("Khong tim thay xe co ma %s.\n", maXeCanXoa);
          }
}

// Menu

void menuXe(BikeList *bike, const char *FilenameBike) {
          int option;
          do {
            printf("\n--------------MENU XE-----------------\n");
            printf("1. Them xe\n");
            printf("2. Hien thi danh sach xe\n");
            printf("3. Sua thong tin xe\n");
            printf("4. Xoa xe\n");
            printf("5. Thoat\n");
            printf("Nhap lua chon cua ban: ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertBike(bike, FilenameBike);
              break;
            case 2:
              if (bike->head == NULL) {
                printf("Danh sach xe rong.\n");
              } else {
                displayBikeHeaders();
                BikeNode *current = bike->head;
                while (current != NULL) {
                  displayBike(current->bike);
                  current = current->next;
                }
              }
              break;
            case 3:
              suaThongTinXe(bike, FilenameBike);
              break;
            case 4:
              deleteBike(bike, FilenameBike);
              break;
            case 5:
              printf("Thoat chuong trinh.\n");
              break;
            default:
              printf("\nLua chon khong hop le, vui long nhap lai\n");
            }
          } while (option != 5);
}

void menuKho(KhoList *kho, const char *FilenameKho) {
          int option;
          do {
            printf("\n--------------MENU KHO-----------------\n");
            printf("\n1. Nhap thong tin kho hang\n");
            printf("\n2. In thong tin kho hang\n");
            printf("\n3. Thoat\n");
            printf("\nMoi ban chon chuc nang: ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertKho(kho, FilenameKho);
              break;
            case 2:
              if (kho->head == NULL) {
                printf("Danh sach kho hang rong.\n");
              } else {
                displayKhoHeaders();
                KhoNode *current = kho->head;
                while (current != NULL) {
                  displayKho(current->kho);
                  current = current->next;
                }
              }
              break;
            case 3:
              printf("\nCam on ban da su dung dich vu cua chung toi\n");
              break;
            default:
              printf("\nLua chon khong hop le, vui long nhap lai\n");
            }
          } while (option != 3);
}

// menuNcc

void uptadeNcc(NccList *ncc, const char *FilenameNcc) {
          char maNccCanSua[10];
          NhaCC nccCanSua;
          printf("\nNhap ma ncc can sua: ");
          scanf("%s", maNccCanSua);
          NccNode *current = ncc->head;
          while (current != NULL) {
            if (strcmp(current->ncc.MaNCC, maNccCanSua) == 0) {
              printf("\nNhap ten ncc: ");
              scanf("%s", nccCanSua.TenNCC);
              printf("Nhap dia chi ncc: ");
              scanf("%s", nccCanSua.diaChi);
              printf("Nhap SDT ncc: ");
              scanf("%s", nccCanSua.SDT);
              printf("Nhap email ncc: ");
              scanf("%s", nccCanSua.email);
              strcpy(current->ncc.TenNCC, nccCanSua.TenNCC);
              strcpy(current->ncc.diaChi, nccCanSua.diaChi);
              strcpy(current->ncc.SDT, nccCanSua.SDT);
              strcpy(current->ncc.email, nccCanSua.email);
              FILE *file = fopen(FilenameNcc, "w");
              if (file == NULL) {
                printf("Khong the mo file.\n");
                return;
              }
              NccNode *temp = ncc->head;
              while (temp != NULL) {
                fprintf(file, "%s,%s,%s,%s,%s\n", temp->ncc.MaNCC,
                        temp->ncc.TenNCC, temp->ncc.diaChi, temp->ncc.SDT,
                        temp->ncc.email);
                temp = temp->next;
              }
              fclose(file);
              printf("Da cap nhat thong tin ncc.\n");
              return;
            } else {
              current = current->next;
            }
          }
          if (current == NULL) {
            printf("Khong tim thay ncc co ma %s.\n", maNccCanSua);
          }
}

void deleteNcc(NccList *ncc, const char *FilenameNcc) {
          char maNccCanXoa[10];
          printf("\nNhap ma ncc can xoa: ");
          scanf("%s", maNccCanXoa);

          NccNode *current = ncc->head;
          NccNode *prev = NULL;

          while (current != NULL) {
            if (strcmp(current->ncc.MaNCC, maNccCanXoa) == 0) {
              if (prev == NULL) {
                ncc->head = current->next;
              } else {
                prev->next = current->next;
              }
              free(current);

              FILE *file = fopen(FilenameNcc, "w");
              if (file == NULL) {
                printf("Khong the mo file.\n");
                return;
              }
              NccNode *temp = ncc->head;
              while (temp != NULL) {
                fprintf(file, "%s,%s,%s,%s,%s\n", temp->ncc.MaNCC,
                        temp->ncc.TenNCC, temp->ncc.diaChi, temp->ncc.SDT,
                        temp->ncc.email);
                temp = temp->next;
              }
              fclose(file);

              printf("Da xoa ncc co ma %s.\n", maNccCanXoa);
              return;
            } else {
              prev = current;
              current = current->next;
            }
          }
}

void menuNcc(NccList *ncchead, const char *Filenamencc) {
          int option;
          NhaCC ncc;
          do {
            printf("\n----------------MENU NHA CUNG CAP----------------\n");
            printf("\n1. Them nha cung cap\n");
            printf("\n2. In danh sach nha cung cap\n");
            printf("\n3. Cap nhat thong tin nha cung cap\n");
            printf("\n4. Xoa nha cung cap\n");
            printf("\n5. Ghi vao File\n");
            printf("\n6. Doc tu File\n");
            printf("\n7. Thoat\n");
            printf("\nNhap lua chon cua ban (1-7): ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertNcc(ncchead, Filenamencc);
              break;
            case 2:
              if (ncchead->head == NULL) {
                printf("Danh sach nha cung cap rong.\n");
              } else {
                displayNccHeaders();
                NccNode *current = ncchead->head;
                while (current != NULL) {
                  displayNcc(current->ncc);
                  current = current->next;
                }
              }
              break;
            case 3:
              uptadeNcc(ncchead, Filenamencc);
              break;
            case 4:
              deleteNcc(ncchead, Filenamencc);
              break;
            case 5:
              break;
            case 6:
              break;
            case 7:
              break;
            default:
              printf("\nLua chon cua ban khong hop le, vui long nhap lai\n");
            }
          } while (option != 7);
}

void menuCuaHang(CuaHangList *chhead, const char *FilenameCuaHang) {
          int option;
          CuaHang Ch;
          do {
            printf("\n----------------MENU CUA HANG----------------\n");
            printf("\n1. Them cua hang\n");
            printf("\n2. Cap nhat thong tin cua hang\n");
            printf("\n3. Xoa cua hang\n");
            printf("\n4. In danh sach cua hang\n");
            printf("\n5. Ghi vao File\n");
            printf("\n6. Doc tu File\n");
            printf("\n7. Thoat\n");
            printf("\nNhap lua chon cua ban (1-7): ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertCuaHang(chhead, FilenameCuaHang);
              break;
            case 2:
              break;
            case 3:
              break;
            case 4:
              break;
            case 5:
              break;
            case 6:
              break;
            case 7:
              printf("\nCam on ban!!!\n");
              break;
            default:
              printf("\nLua chon cua ban khong hop le, vui long nhap lai\n");
            }
          } while (option != 7);
}

// menu Nhan vien
void initNhanVienList(NhanVienList *nvhead) {
          nvhead->head = NULL; }

void updateNhanVien(NhanVienList *nhanVien, const char *FilenameNhanVien) {
          char maNVCanSua[10];
          NhanVien nhanVienCanSua;
          printf("\nNhap ma nhan vien ca sua: ");
          scanf("%s", maNVCanSua);
          NhanVienNode *current = nhanVien->head;
          while (current != NULL) {
            if (strcmp(current->nv.nv.ma, maNVCanSua) == 0) {
              printf("\nNhap ten nhan vien: ");
              scanf("%s", nhanVienCanSua.nv.ten);
              printf("Nhap dia chi nhan vien: ");
              scanf("%s", nhanVienCanSua.nv.diaChi);
              printf("Nhap SDT nhan vien: ");
              scanf("%s", nhanVienCanSua.nv.SDT);
              printf("Nhap email nhan vien: ");
              scanf("%s", nhanVienCanSua.nv.email);
              printf("Nhap gioi tinh nhan vien: ");
              scanf("%s", nhanVienCanSua.gioiTinh);
              printf("Nhap ngay sinh nhan vien: ");
              scanf("%d/%d/%d", &nhanVienCanSua.ngaySinh.Ngay,
                    &nhanVienCanSua.ngaySinh.Thang,
                    &nhanVienCanSua.ngaySinh.Nam);
              strcpy(current->nv.nv.ten, nhanVienCanSua.nv.ten);
              strcpy(current->nv.nv.diaChi, nhanVienCanSua.nv.diaChi);
              strcpy(current->nv.nv.SDT, nhanVienCanSua.nv.SDT);
              strcpy(current->nv.nv.email, nhanVienCanSua.nv.email);
              strcpy(current->nv.gioiTinh, nhanVienCanSua.gioiTinh);
              current->nv.ngaySinh.Ngay = nhanVienCanSua.ngaySinh.Ngay;
            }
          }
}

void deleteNhanVien(NhanVienList *nvhead, const char *Filenamenv) {
          char maNVCanXoa[10];
          printf("\nNhap ma nhan vien can xoa: ");
          scanf("%s", maNVCanXoa);
          NhanVienNode *current = nvhead->head;
          NhanVienNode *prev = NULL;
          while (current != NULL) {
            if (strcmp(current->nv.nv.ma, maNVCanXoa) == 0) {
              if (prev == NULL) {
                nvhead->head = current->next;
              } else {
                prev->next = current->next;
              }
              free(current);
              printf("\nXoa nhan vien co ma %s thanh cong\n", maNVCanXoa);
              return;
            }
            prev = current;
            current = current->next;
          }
          printf("\nKhong tim thay nhan vien co ma %s\n", maNVCanXoa);
}

void ghiDSNV(NhanVienList *nvhead, const char *Filenamenv) {
          FILE *file = fopen(Filenamenv, "w");
          if (file == NULL) {
            printf("\nKhong the mo file!\n");
            return;
          }
          NhanVienNode *current = nvhead->head;
          while (current != NULL) {
            fprintf(file, "%s,%s,%s,%s,%s,%s,%d/%d/%d\n", current->nv.nv.ma,
                    current->nv.nv.ten, current->nv.nv.diaChi,
                    current->nv.nv.SDT, current->nv.nv.email,
                    current->nv.gioiTinh, current->nv.ngaySinh.Ngay,
                    current->nv.ngaySinh.Thang, current->nv.ngaySinh.Nam);
            current = current->next;
          }
          fclose(file);
          printf("\nGhi danh sach nhan vien thanh cong!\n");
}

void docDSNV(NhanVienList *nvhead, const char *Filenamenv) {
          FILE *file = fopen(Filenamenv, "r");
          if (file == NULL) {
            printf("\nKhong the mo file!\n");
            return;
          }
          char line[255];
          while (fgets(line, 255, file) != NULL) {
            NhanVienNode *newNode =
                (NhanVienNode *)malloc(sizeof(NhanVienNode));
            if (newNode == NULL) {
              printf("\nKhong the cap phat bo nho!\n");
              return;
            }
            char *token = strtok(line, ",");
            strcpy(newNode->nv.nv.ma, token);
            token = strtok(NULL, ",");
            strcpy(newNode->nv.nv.ten, token);
            token = strtok(NULL, ",");
            strcpy(newNode->nv.nv.diaChi, token);
            token = strtok(NULL, ",");
            strcpy(newNode->nv.nv.SDT, token);
            token = strtok(NULL, ",");
            strcpy(newNode->nv.nv.email, token);
            token = strtok(NULL, ",");
            strcpy(newNode->nv.gioiTinh, token);
            token = strtok(NULL, ",");
            char temp[10];
            strcpy(temp, token);
            int ngaySinh = atoi(temp);
            newNode->nv.ngaySinh.Ngay = ngaySinh;
            token = strtok(NULL, ",");
            newNode->next = nvhead->head;
            nvhead->head = newNode;
          }
          fclose(file);
          printf("\nDoc danh sach nhan vien thanh cong!\n");
}

void menuNhanVien(NhanVienList *nvhead, const char *Filenamenv) {
          int option;
          NhanVien nv;
          do {
            printf("\n----------------MENU NHAN VIEN----------------\n");
            printf("\n1. Them nhan vien\n");
            printf("\n2. Cap nhat thong tin nhan vien\n");
            printf("\n3. Xoa nhan vien\n");
            printf("\n4. In danh sach nhan vien\n");
            printf("\n5. Ghi vao File\n");
            printf("\n6. Doc tu File\n");
            printf("\n7. Thoat\n");
            printf("\nNhap lua chon cua ban (1-7): ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertNhanVien(nvhead, Filenamenv);
              break;
            case 2:
              updateNhanVien(nvhead, Filenamenv);
              break;
            case 3:
              deleteNhanVien(nvhead, Filenamenv);
              break;
            case 4:
              displayHeaders();
              displayNhanVien(nv);
              break;
            case 5:
              ghiDSNV(nvhead, Filenamenv);
              break;
            case 6:
              docDSNV(nvhead, Filenamenv);
              break;
            case 7:
              printf("\nCam on ban!!!\n");
              break;
            default:
              printf("\nLua chon cua ban khong hop le, vui long nhap lai\n");
            }
          } while (option != 7);
}

void menuKhach(KhachHangList *cshead, const char *Filenamecs) {
          int option;
          KhachHang khach;
          do {
            printf("\n----------------MENU KHACH HANG----------------\n");
            printf("\n1. Them khach hang\n");
            printf("\n2. Duyet danh sach khach hang\n");
            printf("\n3. Cap nhat thong tin khach hang\n");
            printf("\n4. Xoa thong tin khach hang\n");
            printf("\n5. Luu thong tin khach hang vao file\n");
            printf("\n6. In thong tin khach hang tu file\n");
            printf("\n7. Thoat\n");
            printf("\nNhap lua chon cua ban (1-7): ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertKhachHang(cshead, Filenamecs);
              break;
            case 2:
              break;
            case 3:
              break;
            case 4:
              break;
            case 5:
              break;
            case 6:
              break;
            case 7:
              break;
            default:
              printf("\nLua chon khong hop le, vui long nhap lai\n");
            }
          } while (option != 7);
}

void menuHoaDonNhap(HoaDonNhap *hdn, const char *Filenamehdn) {
          int option;
          do {
            printf("\n--------------MENU HOA DON NHAP-----------------\n");
            printf("\n1. Nhap hoa don nhap hang:\n");
            printf("\2. In hoa don nhap hang\n");
            printf("\n3. Ghi vao file\n");
            printf("\n4. Doc tu file\n");
            printf("\n5. Thoat\n");
            printf("\nMoi ban chon chuc nang: ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertHoaDonNhap(hdn, Filenamehdn);
              break;
            case 2:
              break;
            case 3:
              break;
            case 4:
              break;
            case 5:
              break;
            default:
              printf("\nLua chon khong hop le, vui long nhap lai\n");
            }
          } while (option != 5);
}

void menuHoaDonBan(HoaDonBan *hdb, const char *Filenamehdm) {
          int option;
          do {
            printf("\n--------------MENU HOA DON BAN-----------------\n");
            printf("\n1. Nhap hoa don mua hang:\n");
            printf("\n2. In hoa don mua hang\n");
            printf("\n3. Ghi vao file\n");
            printf("\n4. Doc tu file\n");
            printf("\n5. Thoat\n");
            printf("\nMoi ban chon chuc nang: ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertHoaDonBan(hdb, Filenamehdm);
              break;
            case 2:

              break;
            case 3:
              break;
            case 4:
              break;
            case 5:
              break;
            default:
              printf("\nLua chon khong hop le, vui long nhap lai\n");
            }
          } while (option != 5);
}

void menuThongKe(TkList *tkhead, const char *Filenametk) {
          int option;
          do {
            printf("\n----------------MENU THONG KE----------------\n");
            printf("\n1. Thong ke so luong khach hang da mua hang\n");
            printf(
                "\n2. Thong ke so luong mat hang da nhap theo nha cung cap\n");
            printf("\n3. Xem thong ke doanh thu");
            printf("\n4. Thoat\n");
            printf("\nNhap lua chon cua ban (1-4): ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              insertThongKe(tkhead, Filenametk);
              break;
            case 2:
              break;
            case 3:
              break;
            case 4:
              printf("\nCam on ban!!!\n");
              break;
            default:
              printf("\nLua chon cua ban khong hop le, vui long nhap lai\n");
            }
          } while (option != 4);
}

void menuTong(HoaDonNhap *hdn, HoaDonBan *hdb, KhachHangNode *cshead,
              NccNode *ncchead, TkNode *tkhead, NhanVienNode *nvhead,
              CuaHangNode *chhead, KhoNode *khohead) {
          int option;
          do {
            printf("\n--------------MENU TONG-----------------\n");
            printf("1. MENU Hoa don nhap\n");
            printf("2. MENU Hoa don mua\n");
            printf("3. MENU Khach hang\n");
            printf("4. MENU Kho\n");
            printf("5. MENU Nha cung cap\n");
            printf("6. MENU Nhan vien\n");
            printf("7. MENU Thong ke\n");
            printf("8. Thoat\n");
            printf("Nhap lua chon cua ban: ");
            scanf("%d", &option);
            switch (option) {
            case 1:
              menuhdn(hdn, "hoadonnhap.dat");
              break;
            case 2:
              menuhdm(hdb, "hoadonmua.dat"););
              break;
            case 3:
              menuKhach(cshead);
              break;
            case 4:
              menuKho(khohead);
              break;
            case 5:
              menuNcc(ncchead);
              break;
            case 6:
              menuNhanVien(nvhead);
              break;
            case 7:
              menuThongKe(tkhead);
              break;
            case 8:
              printf("\nCam on ban da su dung dich vu cua chung toi\n");
              break;
            default:
              printf("\nLua chon khong hop le, vui long nhap so tu 1 den 8.\n");
            }
          } while (option != 8);
}
// Main

int main() {
  BikeList bikeList;
  TkList tkList;
  KhoList khoList;
  NccList nccList;
  NhanVienList nvList;
  CuaHangList chList;
  KhachHangList csList;
  initList(&bikeList);
  initList(&tkList);
  initList(&khoList);
  initList(&nccList);
  initList(&nvList);
  initList(&chList);
  initList(&csList);
  
  return 0;
)
