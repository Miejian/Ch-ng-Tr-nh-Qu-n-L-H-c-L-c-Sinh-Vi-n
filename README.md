students = []

n = int(input("Nhap so luong sinh vien: "))

for i in range(n):
    print("\nSinh vien", i + 1)

    # Ma sinh vien (so)
    while True:
        masv = input("Ma SV: ")
        if masv.isdigit():
            masv = int(masv)
            break
        else:
            print("Ma SV phai la so!")

    # Ho ten (chu cai)
    while True:
        hoten = input("Ho ten: ")
        if hoten.replace(" ", "").isalpha():
            break
        else:
            print("Ho ten chi duoc la chu!")

    # Diem co so
    while True:
        s = input("Diem co so: ")
        if s.replace(".", "", 1).isdigit():
            diem_cs = float(s)
            break
        else:
            print("Nhap so!")

    # Diem chuyen nganh
    while True:
        s = input("Diem chuyen nganh: ")
        if s.replace(".", "", 1).isdigit():
            diem_cn = float(s)
            break
        else:
            print("Nhap so!")

    students.append([masv, hoten, diem_cs, diem_cn])

while True:
    print("\n1. In danh sach")
    print("2. Diem cao nhat")
    print("3. Diem thap nhat")
    print("4. Sinh vien khong dat")
    print("0. Thoat")

    chon = input("Chon: ")

    if chon == "1":
        print("MaSV      HoTen               DiemCK")
        for sv in students:
            diem_ck = sv[2] * 0.4 + sv[3] * 0.6
            print(f"{sv[0]:<10}{sv[1]:<20}{diem_ck:.2f}")

    elif chon == "2":
        max_sv = students[0]
        max_diem = max_sv[2] * 0.4 + max_sv[3] * 0.6
        for sv in students:
            diem_ck = sv[2] * 0.4 + sv[3] * 0.6
            if diem_ck > max_diem:
                max_diem = diem_ck
                max_sv = sv
        print(max_sv[0], max_sv[1], max_diem)

    elif chon == "3":
        min_sv = students[0]
        min_diem = min_sv[2] * 0.4 + min_sv[3] * 0.6
        for sv in students:
            diem_ck = sv[2] * 0.4 + sv[3] * 0.6
            if diem_ck < min_diem:
                min_diem = diem_ck
                min_sv = sv
        print(min_sv[0], min_sv[1], min_diem)

    elif chon == "4":
        print("MaSV      HoTen               Mon khong dat  Diem")
        for sv in students:
            if sv[2] < 4:
                print(f"{sv[0]:<10}{sv[1]:<20}Co so         {sv[2]}")
            if sv[3] < 4:
                print(f"{sv[0]:<10}{sv[1]:<20}Chuyen nganh  {sv[3]}")

    elif chon == "0":
        break
