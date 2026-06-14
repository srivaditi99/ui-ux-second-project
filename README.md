# ui-ux-second-project
A small portfolio website created to practice HTML and CSS, showcasing a clean homepage layout for a dentistry-focused web design.

This website features a friendly dental homepage with a clear hero section, service highlights, patient benefits, and contact information. It is designed to present essential dentistry services in a simple, professional way.

The stylesheet uses a soft blue accent and clean white content panels to reflect a calm dental office atmosphere. Consistent spacing, rounded corners, and subtle shadows are used to keep the design polished and easy to read on desktop and mobile screens.

---

## Project Structure

```
ui-ux-second-project/
├── HTML/
│   └── mysecond.html          # Main dentistry homepage
├── Stylesheet/
│   └── mysecond.css           # Styling for the homepage
├── README.md                  # This file
└── LICENSE                    # Project license
```

---

## Nginx Setup & Configuration

### Prerequisites
- **Nginx** installed at: `C:\Program Files\Nginx\nginx-1.30.2`
- **Project location**: `C:\Users\Aditi Srivastava\Desktop\workspace\web-dev\ui-ux-second-project`
- **Nginx running** on port 80 with the parent workspace set as root

### Current Nginx Configuration

The following location block has been added to `C:\Program Files\Nginx\nginx-1.30.2\conf\nginx.conf`:

```nginx
server {
    listen       80;
    server_name  localhost;
    
    root "C:/Users/Aditi Srivastava/Desktop/workspace/web-dev";
    
    # ui-ux-first-project (existing)
    location /ui-ux-first-project/ {
        try_files $uri $uri/ =404;
        autoindex on;
    }
    
    # ui-ux-second-project (newly added)
    location /ui-ux-second-project/ {
        try_files $uri $uri/ =404;
        autoindex on;
    }
}
```

**Key points:**
- The Nginx `root` is set to the parent workspace folder: `C:/Users/Aditi Srivastava/Desktop/workspace/web-dev`
- Both projects (`ui-ux-first-project` and `ui-ux-second-project`) are served from their respective subfolders
- Directory autoindex is enabled for browsing folder contents

---

## How to Access the Project

### Step 1: Ensure Nginx is Running

1. Open **Task Manager** or check for `nginx.exe` processes.
2. If not running, open an **elevated Command Prompt** and start Nginx:
   ```
   cd "C:\Program Files\Nginx\nginx-1.30.2"
   start nginx
   ```

### Step 2: Reload Configuration (if you made changes)

After modifying `nginx.conf`, reload Nginx to pick up changes:

```
cd "C:\Program Files\Nginx\nginx-1.30.2"
nginx -s reload
```

**If reload fails**, stop and restart Nginx:

```
taskkill /IM nginx.exe /F
cd "C:\Program Files\Nginx\nginx-1.30.2"
start nginx
```

### Step 3: Access the Website

Open your browser and navigate to:

```
http://localhost/ui-ux-second-project/HTML/mysecond.html
```

**Expected Result:** The Bright Smile Dentistry homepage should load with:
- Header with title and tagline
- Welcome section with service overview
- Services section with detailed offerings
- Why Choose Us section with key benefits
- Contact section with email and phone
- Footer with company info

---

## Troubleshooting

### 404 Not Found Error

**Cause:** Nginx cannot find the requested file.

**Solutions:**
1. Verify file exists: `HTML/mysecond.html` must be present in the project folder
2. Check Nginx root path: Should be `C:/Users/Aditi Srivastava/Desktop/workspace/web-dev`
3. Verify location block is in `nginx.conf` (see Configuration section above)
4. Reload Nginx after any config changes:
   ```
   cd "C:\Program Files\Nginx\nginx-1.30.2"
   nginx -s reload
   ```

### Connection Refused

**Cause:** Nginx is not running or port 80 is blocked.

**Solutions:**
1. Start Nginx:
   ```
   cd "C:\Program Files\Nginx\nginx-1.30.2"
   start nginx
   ```
2. Check for process conflicts on port 80 using elevated Command Prompt:
   ```
   netstat -ano | findstr :80
   ```

### CSS Not Loading

**Cause:** Stylesheet path reference may be incorrect.

**Solution:** Verify the CSS link in `HTML/mysecond.html`:
```html
<link rel="stylesheet" href="../Stylesheet/mysecond.css">
```

The relative path `../Stylesheet/` should correctly point to the parent folder's Stylesheet directory.

---

## Development Notes

### File Naming
- HTML file: `mysecond.html` (not `mysecomd.html`)
- CSS file: `mysecond.css`
- Ensure correct spelling to avoid 404 errors

### CSS Styling Features
- Soft blue accent color reflecting calm dental office atmosphere
- Clean white content panels
- Rounded corners for modern appearance
- Subtle shadows for depth
- Responsive design for desktop and mobile screens
- Consistent spacing and typography

---

## Accessing Other Projects

You can access the first project (if configured) at:

```
http://localhost/ui-ux-first-project/
```

Both projects run on the same Nginx instance and port 80 without conflicts.

---

## Additional Resources

- **Nginx Documentation**: https://nginx.org/en/docs/
- **HTML & CSS Practice**: Use this project to practice semantic HTML and modern CSS techniques
- **Project Goal**: Learn clean web design and professional HTML/CSS structure
