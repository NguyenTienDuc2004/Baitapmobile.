# BÁO CÁO BÀI TẬP LỚN
## MÔN: PHÁT TRIỂN ỨNG DỤNG TRÊN THIẾT BỊ DI ĐỘNG - TEE0419

| Thông tin | Chi tiết |
|-----------|----------|
| **Sinh viên** | Nguyễn Tiến Đức |
| **MSSV** | K225480106081 |
| **Môn học** | TEE0419 - Phát triển ứng dụng trên thiết bị di động |
| **Ngày nộp** | 05/06/2026 |

---

## MỤC LỤC
1. [Phần 1: MIT App Inventor](#phần-1-mit-app-inventor)
2. [Phần 2: Android Studio](#phần-2-android-studio)

---

# PHẦN 1: MIT APP INVENTOR

## Bước 1: Tạo project mới

Truy cập https://ai2.appinventor.mit.edu → Đăng nhập Google → New Project → đặt tên `BaiTap`


> 
<img width="1456" height="819" alt="image" src="https://github.com/user-attachments/assets/c3c32a9f-f4e8-456c-9fba-a3672c6fbd19" />


---

## Bước 2: Thiết kế Screen1 - About

Kéo thả các component trong Designer:
- **Label**: Tên sinh viên "Nguyễn Tiến Đức", FontSize=24, Bold
- **Label**: MSSV "K225480106081", FontSize=16  
- **Button**: "Giải Toán" (màu xanh lá), Width=Fill parent
- **Button**: "Trang Web" (màu xanh dương), Width=Fill parent

**Mô tả thanh công cụ Palette:**
- Palette bên trái chứa các component phân nhóm: User Interface, Layout, Media...
- Kéo component từ Palette → thả vào Viewer → chỉnh Properties bên phải
- Properties cho phép thay đổi: Text, FontSize, BackgroundColor, Width, Height...

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3d2375ee-9f33-4832-8300-67eb288cb7bc" />


---

## Bước 3: Thiết kế Screen2 - Giải Toán

Giải phương trình bậc 1: **ax + b = 0**

Components:
- Label "Giải phương trình: ax + b = 0"
- Label "Nhập a:" + TextBox nhập a (NumbersOnly=true)
- Label "Nhập b:" + TextBox nhập b (NumbersOnly=true)  
- Button "Giải" (màu xanh lá)
- Label hiển thị kết quả (để trống)

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/936fccf6-9dc0-439b-8445-922040f8a1c4" />

---

## Bước 4: Thiết kế Screen3 - WebView

- Kéo **WebViewer** từ User Interface vào màn hình
- Width = Fill parent, Height = Fill parent
- HomeUrl = `https://vietnamnet.vn`

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e0a846f5-6c21-45f1-bf25-16d589039bae" />


---

## Bước 5: Lập trình Blocks

### Blocks Screen1 - Chuyển màn hình
```
when Button1.Click
  open another screen screenName "Screen2"

when Button2.Click
  open another screen screenName "Screen3"
```


**Bản chất của việc kéo thả Block:**
- Mỗi block tương đương 1 câu lệnh hoặc cấu trúc điều kiện trong lập trình
- Block có màu sắc phân loại: vàng=sự kiện, xanh=điều kiện, tím=biến...
- Kéo block từ danh sách trái → thả vào vùng làm việc → ghép các block lại

**Ưu điểm so với viết code:**
- Trực quan, không lo lỗi cú pháp
- Phù hợp người mới học lập trình
- Nhanh tạo prototype

**Nhược điểm:**
- Khó kiểm soát khi logic phức tạp
- Không linh hoạt bằng code thật
- Hiệu năng thấp hơn native code

**Copy-paste Block (Backpack):**
- Backpack (ba lô) ở góc trên phải màn hình Blocks
- Kéo block vào Backpack → chuyển sang screen khác → kéo ra dùng lại

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/31f36857-aa31-4ecd-a761-c78a86103d82" />

### Blocks Screen2 - Giải toán
```
when Button1.Click
  if TextBox1.Text = "0"
    set Label4.Text = "Phương trình vô nghiệm"
  else
    set Label4.Text = (0 - TextBox2.Text) / TextBox1.Text
```

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9ed90a09-c0a5-4d50-95b3-7b8bdaaec0f6" />

---
### Kết quả sau khi làm và test app
<img width="1290" height="2796" alt="image" src="https://github.com/user-attachments/assets/6bcd1cb6-7a50-4d47-ad35-a15be4712bf0" /> <img width="1290" height="2796" alt="image" src="https://github.com/user-attachments/assets/c34d9bf1-17c6-4879-bcfe-620eff71b38e" />

<img width="1290" height="2796" alt="image" src="https://github.com/user-attachments/assets/1f00136a-a72e-43e2-92f3-b890569540dd" />

# PHẦN 2: ANDROID STUDIO

## Bước 6: Tạo Project Android Studio

- New Project → Empty Views Activity
- Name: `Nuyentienduc`, Language: Java, Min SDK: API 24
- Save location: `D:\BaiTapLon`

<img width="1119" height="807" alt="image" src="https://github.com/user-attachments/assets/8cf1775c-ca9f-4a48-b132-c11993c48efb" />


---

## Bước 7: AndroidManifest.xml

`AndroidManifest.xml` mô tả tổng quan về app:
- Tên package (định danh duy nhất)
- Danh sách Activity
- Quyền (Permission) app cần
- Activity nào là màn hình khởi động

**Khai báo quyền INTERNET:**
```xml
<uses-permission android:name="android.permission.INTERNET"/>
```
→ Cho phép app kết nối mạng để gọi API và hiển thị WebView

**Khai báo Activity:**
```xml
<activity android:name=".MainActivity" android:exported="true">
    <intent-filter>
        <action android:name="android.intent.action.MAIN"/>
        <category android:name="android.intent.category.LAUNCHER"/>
    </intent-filter>
</activity>
```

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/59f45d83-e2f2-4516-9157-d7684c7791e8" />


---

## Bước 8: Vòng đời Activity và hàm onCreate

**Vòng đời Activity:**
```
onCreate() → onStart() → onResume() → [Đang chạy]
                                           ↓
                                      onPause() → onStop() → onDestroy()
```
<img width="774" height="591" alt="image" src="https://github.com/user-attachments/assets/8202b85c-4e63-46c4-bb29-f95d85892827" />

**Tại sao có hàm `onCreate()` tự sinh?**

Khi tạo project, Android Studio tự sinh `onCreate()` vì đây là hàm bắt buộc, được gọi đầu tiên khi Activity được tạo. Trong `onCreate()` ta thực hiện:
- `setContentView()`: gắn layout XML
- `findViewById()`: lấy các View
- Thiết lập sự kiện click
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/86cadc64-afcd-4766-a16d-67100da079da" />

---

## Bước 9: Giao diện XML và tham chiếu resource

**Hardcode (không nên):**
```xml
android:text="Xin chào"
```

**Tham chiếu (nên dùng):**
```xml
android:text="@string/xin_chao"
```

**Cú pháp tham chiếu:** `@<type>/<name>`

**Ưu điểm:**
- Thay đổi tập trung tại một chỗ
- OS tự động chọn resource theo LANGUAGE → app đa ngôn ngữ
- OS tự động chọn theo THEME → app hỗ trợ dark/light mode
- OS tự động chọn theo LOCATION → nội dung phù hợp vùng miền

**LinearLayout - Đối tượng chứa:**
```xml
<LinearLayout
    android:orientation="vertical"
    android:gravity="center">
    <!-- View con xếp dọc, căn giữa -->
</LinearLayout>
```
- `orientation="vertical"`: các View con xếp theo chiều dọc
- `orientation="horizontal"`: xếp theo chiều ngang
- `gravity`: căn chỉnh vị trí (center, top, bottom, left, right)

---
<img width="807" height="588" alt="image" src="https://github.com/user-attachments/assets/d73d5905-be88-44ad-bc0d-8fd15fb647ce" />

## Bước 10: Xử lý sự kiện - 2 cách

**Layout cần có `id`:**
```xml
<Button android:id="@+id/btnGiaiToan" .../>
```

**Cách 1: Lambda (ngắn gọn)**
```java
Button btn = findViewById(R.id.btnGiaiToan);
btn.setOnClickListener(v -> {
    Intent intent = new Intent(this, GiaiToanActivity.class);
    startActivity(intent);
});
```

**Cách 2: Implement OnClickListener**
```java
public class MainActivity extends AppCompatActivity 
        implements View.OnClickListener {
    @Override
    public void onClick(View v) {
        if (v.getId() == R.id.btnGiaiToan) {
            // xử lý
        }
    }
}
```

---

## Bước 11: Tạo 3 Activity

Tạo: `MainActivity`, `GiaiToanActivity`, `WebViewActivity`

Chuột phải `com.example.nuyentienduc` → New → Activity → Empty Views Activity


<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5a9dcd03-f683-48a8-8d80-8759477aaab4" />


---

## Bước 12: Activity1 - MainActivity (About)

**activity_main.xml:**
```xml
<LinearLayout orientation="vertical" gravity="center" padding="24dp">
    <TextView text="Nguyễn Tiến Đức" textSize="24sp" textStyle="bold"/>
    <TextView text="MSSV: K225480106081" textSize="16sp"/>
    <Button id="btnGiaiToan" text="Giải Toán"/>
    <Button id="btnWebView" text="Trang Web"/>
</LinearLayout>
```

**Tương tác code với layout:**
```java
Button btnGiaiToan = findViewById(R.id.btnGiaiToan);
btnGiaiToan.setOnClickListener(v -> {
    startActivity(new Intent(this, GiaiToanActivity.class));
});
```

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d9589fbf-32be-4bcc-a800-f60d3184e030" />
<img width="1456" height="819" alt="image" src="https://github.com/user-attachments/assets/a8b4f339-0c9f-4bc5-b846-210089bd8f13" />


---

## Bước 13: Activity2 - Giải Toán + Gọi API

Giải phương trình ax + b = 0, sau đó gửi kết quả lên API.

**Gọi API POST:**
```java
JSONObject input = new JSONObject();
input.put("a", finalA);
input.put("b", finalB);
input.put("c", 0);
input.put("name", "hello tắc kè");

JSONObject output = new JSONObject();
output.put("ketluan", finalKetQua);
output.put("abc", "xyz");
output.put("nghiem", finalNghiem);

JSONObject body = new JSONObject();
body.put("app_by", "K225480106081");
body.put("input", input);
body.put("output", output);
// POST đến https://k58kmt.tdh.io.vn/api
```

**Nhận lại JSON:** `{ok:1, stt:1234}`

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ec8fe9e3-557c-4a91-953c-253ad3fc5309" />
<img width="1456" height="819" alt="image" src="https://github.com/user-attachments/assets/50d66125-ddf3-4b92-8fe5-6fe0bac3cc51" />

---

## Bước 14: Activity3 - WebView

```java
WebView webView = findViewById(R.id.webView);
webView.getSettings().setJavaScriptEnabled(true);
webView.setWebViewClient(new WebViewClient());
webView.loadUrl("https://k58kmt.tdh.io.vn?masv=K225480106081");
```

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1bf0d221-3dc3-4f25-814e-7f2f6facc174" />
<img width="1456" height="819" alt="image" src="https://github.com/user-attachments/assets/d9253084-e7b1-42e3-be9a-cfb9e619c230" />


---

## Bước 15: Assets - App đọc dữ liệu offline

**Thư mục Assets:** `app/src/main/assets/`

Khi build APK, mọi file trong Assets đều đóng gói vào APK → app hoạt động offline.

**Cú pháp truy cập:**
```java
InputStream is = getAssets().open("huongdan.json");
```

**Lợi ích:**
- Hoạt động không cần mạng
- Dữ liệu sẵn có ngay khi cài app
- Phù hợp: hướng dẫn sử dụng, dữ liệu tĩnh

**App hướng dẫn học Android:**
- Dữ liệu: `huongdan.json` chứa 6 bước học
- Đặc thù: mảng JSON, mỗi object có buoc/tieude/mota
- Thuật toán: đọc file → parse JSONArray → duyệt từng object → đưa vào ArrayList
- Hiển thị: `ListView` + `ArrayAdapter`
Design Preview ListView
<img width="1456" height="819" alt="image" src="https://github.com/user-attachments/assets/2ac1eb0f-904f-400c-8a1e-7b00b679ea92" />
AssetsActivity.java code
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/f5158fd4-4f78-4720-bcc8-06e3f118b41a" />

---

## Bước 16: Build APK thành công

Build → Generate App Bundles or APKs → Generate APKs

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e64275db-9730-4316-a7fc-67ebfa0459ac" />


---



## KẾT LUẬN

| Hạng mục | Trạng thái |
|----------|-----------|
| MIT App Inventor - Screen1 About | ✅ |
| MIT App Inventor - Screen2 Giải Toán | ✅ |
| MIT App Inventor - Screen3 WebView | ✅ |
| Android Studio - MainActivity | ✅ |
| Android Studio - GiaiToanActivity + API | ✅ |
| Android Studio - WebViewActivity | ✅ |
| Android Studio - AssetsActivity | ✅ |
| AndroidManifest + INTERNET permission | ✅ |
| Build APK thành công | ✅ |
| Báo cáo .md | ✅ |
