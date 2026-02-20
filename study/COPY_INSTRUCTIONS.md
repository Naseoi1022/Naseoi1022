# 📋 원본 레포 → study 폴더로 복사하는 방법

각 공부 레포를 clone한 뒤, **해당 폴더 안의 파일만** 이 레포의 `study/0x_이름/` 안에 복사하면 됩니다.

---

## 방법 1: 수동으로 한 개씩

1. [frontwork](https://github.com/Naseoi1022/frontwork) 등 원본 레포를 **로컬에 clone**합니다.
2. 그 레포 **안의 파일·폴더 전부**를 선택해서 복사합니다. (`.git` 폴더는 제외)
3. `study/01_frontwork` 같은 **대응하는 폴더**를 열고, 그 안에 붙여넣기합니다.
4. 02~08도 같은 방식으로 반복합니다.

---

## 방법 2: PowerShell로 한 번에 (로컬에 clone 가능할 때)

아래 스크립트는 **Naseoi1022 레포 루트**(`study` 폴더가 있는 곳)에서 실행하면 됩니다.  
임시로 클론한 뒤 내용만 복사하고, 클론한 폴더는 지웁니다.

```powershell
# Naseoi1022 레포 루트에서 실행 (study 폴더의 부모)
$base = "https://github.com/Naseoi1022"
$temp = "../_study_clone_temp"
New-Item -ItemType Directory -Force -Path $temp | Out-Null

# 01_frontwork
git clone --depth 1 "$base/frontwork.git" "$temp/frontwork"
Copy-Item -Path "$temp/frontwork/*" -Destination "study/01_frontwork/" -Recurse -Force
Remove-Item -Path "study/01_frontwork/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/frontwork" -Recurse -Force

# 02_javawork
git clone --depth 1 "$base/javawork.git" "$temp/javawork"
Copy-Item -Path "$temp/javawork/*" -Destination "study/02_javawork/" -Recurse -Force
Remove-Item -Path "study/02_javawork/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/javawork" -Recurse -Force

# 03_jspwork
git clone --depth 1 "$base/jspwork.git" "$temp/jspwork"
Copy-Item -Path "$temp/jspwork/*" -Destination "study/03_jspwork/" -Recurse -Force
Remove-Item -Path "study/03_jspwork/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/jspwork" -Recurse -Force

# 04_oraclework
git clone --depth 1 "$base/oraclework.git" "$temp/oraclework"
Copy-Item -Path "$temp/oraclework/*" -Destination "study/04_oraclework/" -Recurse -Force
Remove-Item -Path "study/04_oraclework/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/oraclework" -Recurse -Force

# 05_Modeling
git clone --depth 1 "$base/Modeling.git" "$temp/Modeling"
Copy-Item -Path "$temp/Modeling/*" -Destination "study/05_Modeling/" -Recurse -Force
Remove-Item -Path "study/05_Modeling/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/Modeling" -Recurse -Force

# 06_reactwork
git clone --depth 1 "$base/reactwork.git" "$temp/reactwork"
Copy-Item -Path "$temp/reactwork/*" -Destination "study/06_reactwork/" -Recurse -Force
Remove-Item -Path "study/06_reactwork/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/reactwork" -Recurse -Force

# 07_springbootwork
git clone --depth 1 "$base/springbootwork.git" "$temp/springbootwork"
Copy-Item -Path "$temp/springbootwork/*" -Destination "study/07_springbootwork/" -Recurse -Force
Remove-Item -Path "study/07_springbootwork/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/springbootwork" -Recurse -Force

# 08_flutterwork
git clone --depth 1 "$base/flutterwork.git" "$temp/flutterwork"
Copy-Item -Path "$temp/flutterwork/*" -Destination "study/08_flutterwork/" -Recurse -Force
Remove-Item -Path "study/08_flutterwork/.git" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item -Path "$temp/flutterwork" -Recurse -Force

Remove-Item -Path $temp -Recurse -Force
Write-Host "Done. Check study/ folders."
```

- **주의:** 각 폴더에 이미 `README.md`가 있으면 덮어쓸 수 있으니, 필요하면 복사 후 `study/0x_이름/README.md`만 다시 확인해 두세요.

---

## 복사 후

- `study/0x_이름/` 안에 원본 레포 **루트의 파일·폴더**만 들어가 있으면 됩니다.
- `.git`은 복사하지 않는 것이 좋습니다 (이 레포 하나만 관리하려면).
- 다 넣었으면 `git add study/` 후 커밋·푸시하면 됩니다.
