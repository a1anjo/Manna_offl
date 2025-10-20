# Website Optimization Guide - Manna Caterers

## Optimizations Applied

### 1. **CSS Loading Optimization**
- **Deferred Non-Critical CSS**: Icons, Swiper, and Fancybox CSS now load with `media="print" onload="this.media='all'"` to prevent render-blocking
- **Preconnect**: Added preconnect links for external domains (Google Fonts, Unicons) to establish early connections
- **Reduced Font Weights**: Optimized Google Fonts to load only necessary weights instead of all variants
  - Before: 100-900 weights for both families + Playwrite CZ
  - After: Only 300-700 weights for essential styles

### 2. **JavaScript Loading Optimization**
- **Deferred Loading**: All non-critical JavaScript files now use `defer` attribute
- Scripts that were deferred:
  - Bootstrap & Popper
  - Font Awesome
  - Swiper slider
  - MixItUp filter
  - Fancy box
  - Parallax
  - GSAP & ScrollTrigger
  - Smooth scroll
  - Custom main.js

### 3. **Video Optimization**
- Added `preload="metadata"` to only load video metadata initially
- Added `playsinline` attribute for better mobile performance
- Added poster image placeholders (need to create these images)

### 4. **Preloader Optimization**
- Reduced preloader delay from 1000ms (1 second) to 500ms (0.5 seconds)
- Faster initial page display

### 5. **Image Optimization**
- Added `loading="lazy"` to all menu images (drinks, starters, desserts)
- Images will only load when they're about to enter the viewport
- Added descriptive alt text for better SEO and accessibility

## Additional Recommendations

### High Priority:

1. **Compress Images**
   ```powershell
   # Install image optimization tools
   # For PNG: Use TinyPNG or similar
   # For JPG: Use JPEGoptim or similar
   ```
   - Compress all images in `assets/images/` folder
   - Target: Reduce file sizes by 50-70% without visible quality loss
   - Consider using WebP format for better compression

2. **Create Video Poster Images**
   - Extract a frame from `Manna.mp4` and save as `assets/images/video-poster.jpg`
   - Extract a frame from `Manna-mob.mp4` and save as `assets/images/video-poster-mobile.jpg`
   - Compress these images heavily (they're just placeholders)

3. **Optimize/Compress Videos**
   - Current videos may be too large
   - Use tools like HandBrake or FFmpeg to reduce video file size:
   ```powershell
   # Example FFmpeg command to compress video
   ffmpeg -i assets/videos/Manna.mp4 -vcodec libx264 -crf 28 assets/videos/Manna-compressed.mp4
   ```

4. **Enable Gzip/Brotli Compression**
   - Configure your web server to compress text files (HTML, CSS, JS)
   - Can reduce file sizes by 70-80%

5. **Minify CSS and JavaScript**
   - Minify `style.css`
   - Already using minified versions of libraries (good!)

### Medium Priority:

6. **Add Cache Headers**
   - Set proper cache-control headers for static assets
   - Example for Apache (.htaccess):
   ```apache
   <IfModule mod_expires.c>
     ExpiresActive On
     ExpiresByType image/jpg "access plus 1 year"
     ExpiresByType image/jpeg "access plus 1 year"
     ExpiresByType image/png "access plus 1 year"
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType application/javascript "access plus 1 month"
   </IfModule>
   ```

7. **Consider a CDN**
   - Use a Content Delivery Network for static assets
   - Reduces latency for users far from your server

8. **Optimize GIF in Preloader**
   - The `Food Served.gif` could be heavy
   - Consider converting to video format or optimized GIF
   - Or use CSS animation instead

### Low Priority:

9. **Remove Unused CSS/JS**
   - Audit and remove any unused library code
   - Use tools like PurgeCSS for CSS cleanup

10. **Add Service Worker**
    - Implement Progressive Web App (PWA) features
    - Cache static assets for offline access

## Performance Metrics to Monitor

Test your site with these tools:
- **Google PageSpeed Insights**: https://pagespeed.web.dev/
- **GTmetrix**: https://gtmetrix.com/
- **WebPageTest**: https://www.webpagetest.org/

Target Metrics:
- First Contentful Paint (FCP): < 1.8s
- Largest Contentful Paint (LCP): < 2.5s
- Total Blocking Time (TBT): < 200ms
- Cumulative Layout Shift (CLS): < 0.1
- Time to Interactive (TTI): < 3.8s

## Quick Wins Checklist

- [x] Defer non-critical CSS
- [x] Defer JavaScript files
- [x] Reduce Google Fonts variants
- [x] Add lazy loading to images
- [x] Optimize video loading
- [x] Reduce preloader delay
- [ ] Compress all images
- [ ] Create and add video poster images
- [ ] Compress video files
- [ ] Enable server compression
- [ ] Minify CSS
- [ ] Add browser caching headers

## Expected Results

After implementing all high-priority optimizations:
- **Page Load Time**: Reduced by 40-60%
- **Initial Load Size**: Reduced by 30-50%
- **Time to Interactive**: Improved by 30-40%
- **Mobile Performance**: Significantly improved

## Need Help?

If you need assistance with any of these optimizations, consider:
1. Using online image compressors (TinyPNG, Squoosh)
2. Using video compression tools (HandBrake, CloudConvert)
3. Consulting with your hosting provider about server-level optimizations
