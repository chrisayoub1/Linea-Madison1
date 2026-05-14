<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Linea Madison — Luxury Linen for Women</title>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        /* ===== RESET & BASE ===== */
        *, *::before, *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: #FDFBF7;
            color: #3D3529;
            line-height: 1.6;
            overflow-x: hidden;
        }

        ::-webkit-scrollbar { width: 5px; }
        ::-webkit-scrollbar-track { background: #FDFBF7; }
        ::-webkit-scrollbar-thumb { background: #C4A882; border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: #8B7355; }

        a {
            text-decoration: none;
            color: inherit;
        }

        img {
            display: block;
            max-width: 100%;
        }

        /* ===== TYPOGRAPHY ===== */
        .font-heading {
            font-family: 'Cormorant Garamond', serif;
        }

        /* ===== ANIMATIONS ===== */
        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slowZoom {
            0% { transform: scale(1); }
            100% { transform: scale(1.08); }
        }

        @keyframes widthGrow {
            from { width: 0; }
            to { width: 80px; }
        }

        @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        .animate-fade-up {
            opacity: 0;
            animation: fadeUp 1.2s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
        }

        .animate-fade-in {
            opacity: 0;
            animation: fadeIn 1.5s ease forwards;
        }

        .animate-slow-zoom {
            animation: slowZoom 20s ease-in-out infinite alternate;
        }

        .animate-width-grow {
            animation: widthGrow 1.5s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
        }

        .delay-3 { animation-delay: 0.3s; }
        .delay-5 { animation-delay: 0.5s; }
        .delay-7 { animation-delay: 0.7s; }
        .delay-9 { animation-delay: 0.9s; }
        .delay-15 { animation-delay: 1.5s; }

        /* ===== SCROLL REVEAL ===== */
        .scroll-reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 1s cubic-bezier(0.2, 0.8, 0.2, 1);
        }

        .scroll-reveal.revealed {
            opacity: 1;
            transform: translateY(0);
        }

        /* ===== UTILITY ===== */
        .line-accent {
            width: 80px;
            height: 1px;
            background: #C4A882;
        }

        .line-accent-center {
            width: 80px;
            height: 1px;
            background: #C4A882;
            margin: 0 auto;
        }

        .container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 24px;
        }

        @media (min-width: 768px) {
            .container {
                padding: 0 48px;
            }
        }

        /* ===== NAVIGATION ===== */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 100;
            transition: all 0.5s ease;
        }

        .navbar-inner {
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            height: 80px;
        }

        @media (min-width: 768px) {
            .navbar-inner { padding: 0 48px; }
        }

        .nav-logo {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.75rem;
            font-weight: 300;
            letter-spacing: 0.1em;
            color: #6B5B45;
            text-shadow: 0 0 20px rgba(253,251,247,0.95), 0 0 40px rgba(253,251,247,0.8), 0 1px 3px rgba(253,251,247,0.9);
            transition: all 0.3s ease;
        }

        .nav-links {
            display: none;
            align-items: center;
            gap: 40px;
        }

        @media (min-width: 768px) {
            .nav-links { display: flex; }
        }

        .nav-link {
            position: relative;
            font-size: 0.7rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            font-weight: 300;
            color: #6B5B45;
            text-shadow: 0 0 20px rgba(253,251,247,0.95), 0 0 40px rgba(253,251,247,0.8), 0 1px 3px rgba(253,251,247,0.9);
            transition: all 0.3s ease;
        }

        .nav-link:hover {
            color: #3D3529;
        }

        .nav-link::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 0;
            height: 1px;
            background: #C4A882;
            transition: width 0.4s cubic-bezier(0.2, 0.8, 0.2, 1);
        }

        .nav-link:hover::after {
            width: 100%;
        }

        /* Scrolled state */
        .navbar.scrolled {
            background: rgba(253, 251, 247, 0.96);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border-bottom: 1px solid rgba(232, 223, 208, 0.4);
        }

        .navbar.scrolled .nav-logo,
        .navbar.scrolled .nav-link {
            text-shadow: none;
        }

        .navbar.scrolled .nav-link {
            color: #8B7355;
        }

        .navbar.scrolled .nav-link:hover {
            color: #6B5B45;
        }

        /* Mobile menu button */
        .mobile-menu-btn {
            display: block;
            background: none;
            border: none;
            cursor: pointer;
            color: #6B5B45;
            text-shadow: 0 0 20px rgba(253,251,247,0.95), 0 0 40px rgba(253,251,247,0.8);
            padding: 4px;
        }

        @media (min-width: 768px) {
            .mobile-menu-btn { display: none; }
        }

        .navbar.scrolled .mobile-menu-btn {
            text-shadow: none;
        }

        .mobile-menu {
            display: none;
            background: rgba(253, 251, 247, 0.98);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-top: 1px solid rgba(232, 223, 208, 0.3);
            padding: 32px 24px;
        }

        .mobile-menu.open {
            display: block;
        }

        .mobile-menu a {
            display: block;
            font-size: 0.7rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            color: #8B7355;
            font-weight: 300;
            padding: 12px 0;
            transition: color 0.3s ease;
        }

        .mobile-menu a:hover {
            color: #6B5B45;
        }

        /* Hamburger icon via CSS */
        .hamburger {
            width: 24px;
            height: 16px;
            position: relative;
        }

        .hamburger span {
            display: block;
            width: 100%;
            height: 1.5px;
            background: #6B5B45;
            position: absolute;
            left: 0;
            transition: all 0.3s ease;
        }

        .hamburger span:nth-child(1) { top: 0; }
        .hamburger span:nth-child(2) { top: 7px; }
        .hamburger span:nth-child(3) { top: 14px; }

        .navbar.scrolled .hamburger span {
            background: #6B5B45;
        }

        /* ===== HERO SECTION ===== */
        .hero {
            position: relative;
            min-height: 100vh;
            display: flex;
            align-items: center;
            overflow: hidden;
        }

        .hero-bg {
            position: absolute;
            inset: 0;
        }

        .hero-bg img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            animation: slowZoom 20s ease-in-out infinite alternate;
        }

        .hero-overlay {
            position: absolute;
            inset: 0;
            background: linear-gradient(
                135deg,
                rgba(253,251,247,0.97) 0%,
                rgba(253,251,247,0.90) 30%,
                rgba(253,251,247,0.60) 60%,
                rgba(253,251,247,0.25) 100%
            );
        }

        .hero-content {
            position: relative;
            z-index: 10;
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 24px;
            width: 100%;
        }

        @media (min-width: 768px) {
            .hero-content { padding: 0 48px; }
        }

        .hero-inner {
            max-width: 640px;
        }

        .hero-eyebrow {
            font-size: 0.7rem;
            letter-spacing: 0.35em;
            text-transform: uppercase;
            color: #B5976B;
            font-weight: 300;
            margin-bottom: 24px;
            text-shadow: 0 0 20px rgba(253,251,247,0.95), 0 2px 40px rgba(253,251,247,0.8);
        }

        .hero-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 3rem;
            font-weight: 300;
            line-height: 0.95;
            letter-spacing: -0.02em;
            color: #6B5B45;
            text-shadow: 0 2px 30px rgba(253,251,247,0.95), 0 4px 60px rgba(253,251,247,0.8);
        }

        @media (min-width: 768px) {
            .hero-title { font-size: 4.5rem; }
        }

        @media (min-width: 1024px) {
            .hero-title { font-size: 6rem; }
        }

        .hero-title em {
            font-style: italic;
            color: #B5976B;
        }

        .hero-line {
            margin-top: 32px;
            margin-bottom: 24px;
        }

        .hero-body {
            font-size: 0.875rem;
            font-weight: 300;
            color: #8B7355;
            line-height: 1.7;
            max-width: 440px;
            text-shadow: 0 1px 15px rgba(253,251,247,0.95), 0 2px 30px rgba(253,251,247,0.7);
        }

        @media (min-width: 768px) {
            .hero-body { font-size: 1rem; }
        }

        .hero-cta {
            display: inline-flex;
            align-items: center;
            gap: 12px;
            margin-top: 32px;
            transition: all 0.3s ease;
        }

        .hero-cta:hover .cta-text {
            color: #B5976B;
        }

        .hero-cta:hover .cta-circle {
            background: rgba(196, 168, 130, 0.15);
        }

        .cta-text {
            font-size: 0.7rem;
            letter-spacing: 0.25em;
            text-transform: uppercase;
            color: #6B5B45;
            font-weight: 300;
            transition: color 0.3s ease;
            text-shadow: 0 1px 15px rgba(253,251,247,0.95), 0 2px 30px rgba(253,251,247,0.7);
        }

        .cta-circle {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 1px solid rgba(196, 168, 130, 0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(253, 251, 247, 0.3);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            transition: all 0.3s ease;
        }

        .cta-circle svg {
            width: 14px;
            height: 14px;
            stroke: #6B5B45;
            transition: stroke 0.3s ease;
        }

        .hero-cta:hover .cta-circle svg {
            stroke: #B5976B;
        }

        /* Scroll indicator */
        .scroll-indicator {
            position: absolute;
            bottom: 32px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
        }

        .scroll-line {
            width: 1px;
            height: 48px;
            background: linear-gradient(to bottom, transparent, #C4A882, transparent);
        }

        /* ===== MARQUEE ===== */
        .marquee {
            padding: 24px 0;
            background: #F5F0E8;
            border-top: 1px solid rgba(232, 223, 208, 0.3);
            border-bottom: 1px solid rgba(232, 223, 208, 0.3);
            overflow: hidden;
        }

        .marquee-track {
            display: flex;
            animation: marquee 30s linear infinite;
        }

        .marquee-item {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.1rem;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            color: rgba(196, 168, 130, 0.4);
            white-space: nowrap;
            padding: 0 24px;
        }

        .marquee-dot {
            color: rgba(196, 168, 130, 0.3);
            padding: 0 12px;
        }

        /* ===== COLLECTION SECTION ===== */
        .collection {
            padding: 96px 0;
            background: #FDFBF7;
        }

        @media (min-width: 768px) {
            .collection { padding: 128px 0; }
        }

        .section-eyebrow {
            font-size: 0.7rem;
            letter-spacing: 0.35em;
            text-transform: uppercase;
            color: #B5976B;
            font-weight: 300;
            margin-bottom: 16px;
        }

        .section-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2.5rem;
            font-weight: 300;
            color: #6B5B45;
            letter-spacing: -0.02em;
        }

        @media (min-width: 768px) {
            .section-title { font-size: 3rem; }
        }

        @media (min-width: 1024px) {
            .section-title { font-size: 3.75rem; }
        }

        .section-title em {
            font-style: italic;
            color: #B5976B;
        }

        .text-center {
            text-align: center;
        }

        .collection-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 24px;
            margin-top: 64px;
        }

        @media (min-width: 768px) {
            .collection-grid {
                grid-template-columns: 1fr 1fr;
                gap: 32px;
            }
        }

        .collection-card {
            position: relative;
            overflow: hidden;
            border-radius: 16px;
            cursor: pointer;
        }

        .collection-card-tall {
            aspect-ratio: 4/5;
        }

        .collection-card-wide {
            aspect-ratio: 21/9;
        }

        @media (min-width: 768px) {
            .collection-card-wide {
                grid-column: 1 / -1;
            }
        }

        .collection-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.7s ease-out;
        }

        .collection-card:hover img {
            transform: scale(1.06);
        }

        .collection-gradient {
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(107,91,69,0.6), rgba(107,91,69,0.1), transparent);
        }

        .collection-card-wide .collection-gradient {
            background: linear-gradient(to top, rgba(107,91,69,0.5), rgba(107,91,69,0.05), transparent);
        }

        .collection-card-content {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            padding: 32px;
        }

        @media (min-width: 768px) {
            .collection-card-content { padding: 40px; }
        }

        .collection-card-wide .collection-card-content {
            padding: 32px;
        }

        @media (min-width: 768px) {
            .collection-card-wide .collection-card-content { padding: 48px; }
        }

        .collection-tag {
            font-size: 0.7rem;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            color: rgba(232, 223, 208, 0.8);
            margin-bottom: 8px;
        }

        .collection-name {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.875rem;
            font-weight: 300;
            color: #fff;
        }

        @media (min-width: 768px) {
            .collection-name { font-size: 2.25rem; }
        }

        .collection-card-wide .collection-name {
            font-size: 1.875rem;
        }

        @media (min-width: 768px) {
            .collection-card-wide .collection-name { font-size: 3rem; }
        }

        .collection-discover {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-top: 16px;
            font-size: 0.7rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            color: rgba(232, 223, 208, 0.7);
            transition: letter-spacing 0.5s ease;
        }

        .collection-card:hover .collection-discover {
            letter-spacing: 0.3em;
        }

        .collection-discover svg {
            width: 12px;
            height: 12px;
            stroke: currentColor;
        }

        /* ===== GALLERY SECTION ===== */
        .gallery {
            padding: 96px 0;
            background: #F5F0E8;
        }

        @media (min-width: 768px) {
            .gallery { padding: 128px 0; }
        }

        .gallery-header {
            display: flex;
            flex-direction: column;
            gap: 24px;
            margin-bottom: 64px;
        }

        @media (min-width: 768px) {
            .gallery-header {
                flex-direction: row;
                align-items: flex-end;
                justify-content: space-between;
                margin-bottom: 96px;
            }
        }

        .gallery-header-right {
            font-size: 0.875rem;
            font-weight: 300;
            color: rgba(139, 115, 85, 0.7);
            max-width: 384px;
            line-height: 1.7;
        }

        .gallery-main {
            display: grid;
            grid-template-columns: 1fr;
            gap: 16px;
        }

        @media (min-width: 768px) {
            .gallery-main {
                grid-template-columns: 7fr 5fr;
                gap: 24px;
            }
        }

        .gallery-right {
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        @media (min-width: 768px) {
            .gallery-right { gap: 24px; }
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 16px;
            cursor: pointer;
        }

        .gallery-item-lg {
            aspect-ratio: 4/3;
        }

        .gallery-item-portrait {
            aspect-ratio: 3/4;
        }

        .gallery-item-landscape {
            aspect-ratio: 3/2;
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.7s ease-out;
        }

        .gallery-item:hover img {
            transform: scale(1.05);
        }

        .gallery-hover-overlay {
            position: absolute;
            inset: 0;
            background: rgba(107, 91, 69, 0.2);
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        .gallery-item:hover .gallery-hover-overlay {
            opacity: 1;
        }

        .gallery-badge {
            position: absolute;
            top: 24px;
            left: 24px;
            background: rgba(253, 251, 247, 0.9);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            padding: 8px 16px;
            border-radius: 9999px;
            font-size: 0.7rem;
            letter-spacing: 0.15em;
            text-transform: uppercase;
            color: #8B7355;
            font-weight: 300;
        }

        .gallery-bottom {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
            margin-top: 16px;
        }

        @media (min-width: 768px) {
            .gallery-bottom {
                grid-template-columns: 1fr 1fr 1fr;
                gap: 24px;
                margin-top: 24px;
            }
        }

        .gallery-square {
            aspect-ratio: 1/1;
        }

        .gallery-hide-mobile {
            display: none;
        }

        @media (min-width: 768px) {
            .gallery-hide-mobile { display: block; }
        }

        /* ===== QUOTE SECTION ===== */
        .quote-section {
            padding: 80px 0;
            background: #FDFBF7;
            position: relative;
            overflow: hidden;
        }

        @media (min-width: 768px) {
            .quote-section { padding: 112px 0; }
        }

        .quote-bg {
            position: absolute;
            inset: 0;
            opacity: 0.03;
        }

        .quote-bg img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .quote-content {
            position: relative;
            z-index: 10;
            max-width: 896px;
            margin: 0 auto;
            text-align: center;
            padding: 0 24px;
        }

        .quote-icon {
            color: rgba(196, 168, 130, 0.4);
            margin-bottom: 32px;
        }

        .quote-icon svg {
            width: 40px;
            height: 40px;
        }

        .quote-text {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.875rem;
            font-weight: 300;
            color: #6B5B45;
            line-height: 1.4;
            font-style: italic;
        }

        @media (min-width: 768px) {
            .quote-text { font-size: 2.25rem; }
        }

        @media (min-width: 1024px) {
            .quote-text { font-size: 3rem; }
        }

        .quote-attr {
            font-size: 0.7rem;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            color: #B5976B;
            font-weight: 300;
            margin-top: 16px;
        }

        /* ===== ABOUT SECTION ===== */
        .about {
            padding: 96px 0;
            background: #F5F0E8;
        }

        @media (min-width: 768px) {
            .about { padding: 128px 0; }
        }

        .about-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 48px;
            align-items: center;
        }

        @media (min-width: 768px) {
            .about-grid {
                grid-template-columns: 1fr 1fr;
                gap: 80px;
            }
        }

        .about-image-wrap {
            position: relative;
        }

        .about-image {
            overflow: hidden;
            border-radius: 16px;
            aspect-ratio: 3/4;
        }

        .about-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .about-deco {
            position: absolute;
            bottom: -16px;
            right: -16px;
            width: 128px;
            height: 128px;
            border: 1px solid rgba(196, 168, 130, 0.3);
            border-radius: 16px;
            z-index: -1;
        }

        .about-badge {
            position: absolute;
            top: -16px;
            left: -16px;
            background: #FDFBF7;
            padding: 12px 20px;
            border-radius: 12px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
            border: 1px solid rgba(232, 223, 208, 0.3);
        }

        .about-badge-title {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.875rem;
            font-weight: 300;
            color: #6B5B45;
        }

        .about-badge-sub {
            font-size: 0.7rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            color: #B5976B;
        }

        .about-text p {
            font-size: 0.875rem;
            font-weight: 300;
            color: rgba(139, 115, 85, 0.8);
            line-height: 1.8;
            margin-bottom: 24px;
        }

        @media (min-width: 768px) {
            .about-text p { font-size: 1rem; }
        }

        .about-values {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 24px;
            margin-top: 40px;
            padding-top: 40px;
            border-top: 1px solid rgba(232, 223, 208, 0.4);
        }

        .about-value-icon {
            color: #C4A882;
            margin-bottom: 12px;
        }

        .about-value-icon svg {
            width: 20px;
            height: 20px;
        }

        .about-value-label {
            font-size: 0.7rem;
            letter-spacing: 0.15em;
            text-transform: uppercase;
            color: #6B5B45;
            font-weight: 300;
        }

        .about-value-desc {
            font-size: 0.7rem;
            color: #A69B8C;
            margin-top: 4px;
        }

        /* ===== CONTACT SECTION ===== */
        .contact {
            padding: 96px 0;
            background: #FDFBF7;
            position: relative;
        }

        @media (min-width: 768px) {
            .contact { padding: 128px 0; }
        }

        .contact-bg {
            position: absolute;
            inset: 0;
            opacity: 0.02;
        }

        .contact-bg img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .contact-content {
            position: relative;
            z-index: 10;
            max-width: 896px;
            margin: 0 auto;
            text-align: center;
            padding: 0 24px;
        }

        .contact-desc {
            font-size: 0.875rem;
            font-weight: 300;
            color: rgba(139, 115, 85, 0.7);
            max-width: 448px;
            margin: 0 auto 64px;
            line-height: 1.7;
        }

        .contact-cards {
            display: grid;
            grid-template-columns: 1fr;
            gap: 24px;
        }

        @media (min-width: 768px) {
            .contact-cards {
                grid-template-columns: 1fr 1fr 1fr;
                gap: 24px;
            }
        }

        .contact-card {
            display: block;
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            border: 1px solid rgba(232, 223, 208, 0.4);
            border-radius: 16px;
            padding: 32px;
            transition: all 0.5s ease;
        }

        .contact-card:hover {
            box-shadow: 0 10px 30px rgba(196, 168, 130, 0.1);
            border-color: rgba(196, 168, 130, 0.4);
        }

        .contact-icon-wrap {
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: #F5F0E8;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            transition: background 0.5s ease;
        }

        .contact-card:hover .contact-icon-wrap {
            background: rgba(196, 168, 130, 0.1);
        }

        .contact-icon-wrap svg {
            width: 24px;
            height: 24px;
            fill: #B5976B;
            transition: fill 0.3s ease;
        }

        .contact-card:hover .contact-icon-wrap svg {
            fill: #6B5B45;
        }

        .contact-icon-wrap .stroke-icon {
            fill: none;
            stroke: #B5976B;
            transition: stroke 0.3s ease;
        }

        .contact-card:hover .contact-icon-wrap .stroke-icon {
            stroke: #6B5B45;
        }

        .contact-card-label {
            font-size: 0.7rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            color: #A69B8C;
            margin-bottom: 8px;
        }

        .contact-card-value {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.25rem;
            color: #6B5B45;
            font-weight: 300;
            word-break: break-all;
        }

        /* ===== FOOTER ===== */
        .footer {
            background: #6B5B45;
            color: rgba(232, 223, 208, 0.8);
            padding: 64px 0;
        }

        @media (min-width: 768px) {
            .footer { padding: 80px 0; }
        }

        .footer-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 48px;
            margin-bottom: 64px;
        }

        @media (min-width: 768px) {
            .footer-grid {
                grid-template-columns: 5fr 3fr 4fr;
                gap: 0;
            }
        }

        .footer-brand-name {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.875rem;
            font-weight: 300;
            color: #fff;
            letter-spacing: 0.1em;
            margin-bottom: 16px;
        }

        .footer-brand-line {
            width: 40px;
            height: 1px;
            background: rgba(196, 168, 130, 0.4);
            margin-bottom: 16px;
        }

        .footer-brand-desc {
            font-size: 0.875rem;
            font-weight: 300;
            color: rgba(232, 223, 208, 0.6);
            line-height: 1.7;
            max-width: 384px;
        }

        .footer-heading {
            font-size: 0.7rem;
            letter-spacing: 0.25em;
            text-transform: uppercase;
            color: rgba(196, 168, 130, 0.8);
            margin-bottom: 16px;
        }

        .footer-nav a {
            display: block;
            font-size: 0.875rem;
            font-weight: 300;
            color: rgba(232, 223, 208, 0.5);
            padding: 6px 0;
            transition: color 0.3s ease;
        }

        .footer-nav a:hover {
            color: #E8DFD0;
        }

        .footer-social a {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 0.875rem;
            font-weight: 300;
            color: rgba(232, 223, 208, 0.5);
            padding: 6px 0;
            transition: color 0.3s ease;
        }

        .footer-social a:hover {
            color: #E8DFD0;
        }

        .footer-social svg {
            width: 16px;
            height: 16px;
            flex-shrink: 0;
        }

        .footer-divider {
            height: 1px;
            background: rgba(232, 223, 208, 0.1);
            margin-bottom: 32px;
        }

        .footer-bottom {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 16px;
        }

        @media (min-width: 768px) {
            .footer-bottom {
                flex-direction: row;
                justify-content: space-between;
            }
        }

        .footer-bottom p {
            font-size: 0.7rem;
            font-weight: 300;
            color: rgba(232, 223, 208, 0.3);
        }
    </style>
</head>
<body>

    <!-- ===== NAVIGATION ===== -->
    <nav class="navbar" id="navbar">
        <div class="navbar-inner">
            <a href="#" class="nav-logo">LINEA MADISON</a>

            <div class="nav-links">
                <a href="#collection" class="nav-link">Collection</a>
                <a href="#gallery" class="nav-link">Gallery</a>
                <a href="#about" class="nav-link">About</a>
                <a href="#contact" class="nav-link">Contact</a>
            </div>

            <button class="mobile-menu-btn" id="mobileMenuBtn" aria-label="Menu">
                <div class="hamburger">
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </button>
        </div>

        <div class="mobile-menu" id="mobileMenu">
            <a href="#collection">Collection</a>
            <a href="#gallery">Gallery</a>
            <a href="#about">About</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <!-- ===== HERO ===== -->
    <section class="hero">
        <div class="hero-bg">
            <img src="https://z-cdn-media.chatglm.cn/files/7ffc9999-afe1-409a-9f40-e4e188e240fe.png?auth_key=1878771993-3cbc9970014f49f19f147426a687ac15-0-5c0bc760f5549dcdc7f040fba653c80d"
                 alt="Linea Madison Storefront">
            <div class="hero-overlay"></div>
        </div>

        <div class="hero-content">
            <div class="hero-inner">
                <p class="hero-eyebrow animate-fade-up delay-3">Luxury Linen — Crafted with Intention</p>

                <h1 class="hero-title animate-fade-up delay-5">
                    The Art of<br><em>Effortless</em><br>Elegance
                </h1>

                <div class="hero-line animate-fade-up delay-7">
                    <div class="line-accent animate-width-grow delay-9"></div>
                </div>

                <p class="hero-body animate-fade-up delay-7">
                    Premium linen collections designed for the modern woman who values timeless sophistication and natural beauty.
                </p>

                <a href="#collection" class="hero-cta animate-fade-up delay-9">
                    <span class="cta-text">Explore Collection</span>
                    <span class="cta-circle">
                        <svg viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M12 5v14M19 12l-7 7-7-7"/>
                        </svg>
                    </span>
                </a>
            </div>
        </div>

        <div class="scroll-indicator animate-fade-in delay-15">
            <div class="scroll-line"></div>
        </div>
    </section>

    <!-- ===== MARQUEE ===== -->
    <div class="marquee">
        <div class="marquee-track">
            <span class="marquee-item">Linea Madison</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Luxury Linen</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Timeless Elegance</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Natural Fabrics</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Crafted with Care</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Linea Madison</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Luxury Linen</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Timeless Elegance</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Natural Fabrics</span>
            <span class="marquee-dot">✦</span>
            <span class="marquee-item">Crafted with Care</span>
            <span class="marquee-dot">✦</span>
        </div>
    </div>

    <!-- ===== COLLECTION ===== -->
    <section id="collection" class="collection">
        <div class="container">
            <div class="scroll-reveal text-center">
                <p class="section-eyebrow">Our Collections</p>
                <h2 class="section-title">Curated in <em>Linen</em></h2>
                <div class="line-accent-center" style="margin-top:24px;"></div>
            </div>

            <div class="collection-grid">
                <!-- Card 1 -->
                <div class="collection-card collection-card-tall scroll-reveal">
                    <img src="https://z-cdn-media.chatglm.cn/files/fd13178c-8df0-427d-b511-283ab1a03be6.png?auth_key=1878771993-335f027ff7394c5dbdbef0148c11dda4-0-0cb53d75496158a21954a1b25d385d1c"
                         alt="Linen Fabric Collection">
                    <div class="collection-gradient"></div>
                    <div class="collection-card-content">
                        <p class="collection-tag">Spring / Summer</p>
                        <h3 class="collection-name">Fabric Stories</h3>
                        <div class="collection-discover">
                            <span>Discover</span>
                            <svg viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
                        </div>
                    </div>
                </div>

                <!-- Card 2 -->
                <div class="collection-card collection-card-tall scroll-reveal">
                    <img src="https://z-cdn-media.chatglm.cn/files/471f4e50-c43d-43a9-b4d1-9e3cbbf96ebc.png?auth_key=1878771993-474ddef1f51b42f687819eb63ea72bff-0-cde39d90ff10e8f31f8a7c3980a3e826"
                         alt="Linen Textures & Tones">
                    <div class="collection-gradient"></div>
                    <div class="collection-card-content">
                        <p class="collection-tag">Essential Edit</p>
                        <h3 class="collection-name">Texture & Tone</h3>
                        <div class="collection-discover">
                            <span>Discover</span>
                            <svg viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
                        </div>
                    </div>
                </div>

                <!-- Card 3 - Wide -->
                <div class="collection-card collection-card-wide scroll-reveal">
                    <img src="https://z-cdn-media.chatglm.cn/files/e986d14a-ee74-48a1-9fc6-b7fa1329fb68.png?auth_key=1878771993-d2c7fb4316ec48339360e023847e0b4c-0-77f4e328953c64c2160832658895b3e1"
                         alt="Linea Madison Boutique">
                    <div class="collection-gradient"></div>
                    <div class="collection-card-content">
                        <p class="collection-tag">Visit Us</p>
                        <h3 class="collection-name">The Boutique</h3>
                        <div class="collection-discover">
                            <span>Explore</span>
                            <svg viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===== GALLERY ===== -->
    <section id="gallery" class="gallery">
        <div class="container">
            <div class="gallery-header scroll-reveal">
                <div>
                    <p class="section-eyebrow">Lifestyle</p>
                    <h2 class="section-title">Living in <em>Linen</em></h2>
                </div>
                <p class="gallery-header-right">
                    Every piece is designed to move with you — from quiet mornings at home to sunlit afternoons in the city.
                </p>
            </div>

            <!-- Main Gallery Grid -->
            <div class="gallery-main scroll-reveal">
                <!-- Large Feature -->
                <div class="gallery-item gallery-item-lg">
                    <img src="https://z-cdn-media.chatglm.cn/files/84e5295d-4629-4e78-80b4-6e4fbb8cf5ce.png?auth_key=1878771993-474c9e3657e44514b3a608579d1ccb43-0-ac18650f1c767815c1fd1e9e5ac3efe5"
                         alt="Linen Lifestyle">
                    <div class="gallery-hover-overlay"></div>
                    <span class="gallery-badge">At Home</span>
                </div>

                <!-- Right Column -->
                <div class="gallery-right">
                    <div class="gallery-item gallery-item-portrait scroll-reveal">
                        <img src="https://z-cdn-media.chatglm.cn/files/7ffc9999-afe1-409a-9f40-e4e188e240fe.png?auth_key=1878771993-3cbc9970014f49f19f147426a687ac15-0-5c0bc760f5549dcdc7f040fba653c80d"
                             alt="Linea Madison Window">
                        <div class="gallery-hover-overlay"></div>
                        <span class="gallery-badge">Boutique</span>
                    </div>

                    <div class="gallery-item gallery-item-landscape scroll-reveal">
                        <img src="https://z-cdn-media.chatglm.cn/files/fd13178c-8df0-427d-b511-283ab1a03be6.png?auth_key=1878771993-335f027ff7394c5dbdbef0148c11dda4-0-0cb53d75496158a21954a1b25d385d1c"
                             alt="Linen Textures">
                        <div class="gallery-hover-overlay"></div>
                        <span class="gallery-badge">Textures</span>
                    </div>
                </div>
            </div>

            <!-- Bottom Row -->
            <div class="gallery-bottom scroll-reveal">
                <div class="gallery-item gallery-square">
                    <img src="https://z-cdn-media.chatglm.cn/files/471f4e50-c43d-43a9-b4d1-9e3cbbf96ebc.png?auth_key=1878771993-474ddef1f51b42f687819eb63ea72bff-0-cde39d90ff10e8f31f8a7c3980a3e826"
                         alt="Curated Details">
                    <div class="gallery-hover-overlay"></div>
                </div>

                <div class="gallery-item gallery-square">
                    <img src="https://z-cdn-media.chatglm.cn/files/e986d14a-ee74-48a1-9fc6-b7fa1329fb68.png?auth_key=1878771993-d2c7fb4316ec48339360e023847e0b4c-0-77f4e328953c64c2160832658895b3e1"
                         alt="Storefront Details">
                    <div class="gallery-hover-overlay"></div>
                </div>

                <div class="gallery-item gallery-square gallery-hide-mobile">
                    <img src="https://z-cdn-media.chatglm.cn/files/84e5295d-4629-4e78-80b4-6e4fbb8cf5ce.png?auth_key=1878771993-474c9e3657e44514b3a608579d1ccb43-0-ac18650f1c767815c1fd1e9e5ac3efe5"
                         alt="Living in Linen">
                    <div class="gallery-hover-overlay"></div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===== QUOTE ===== -->
    <section class="quote-section">
        <div class="quote-bg">
            <img src="https://z-cdn-media.chatglm.cn/files/471f4e50-c43d-43a9-b4d1-9e3cbbf96ebc.png?auth_key=1878771993-474ddef1f51b42f687819eb63ea72bff-0-cde39d90ff10e8f31f8a7c3980a3e826" alt="">
        </div>
        <div class="quote-content scroll-reveal">
            <div class="quote-icon">
                <svg viewBox="0 0 24 24" fill="currentColor"><path d="M11 7.05C9.05 8.03 7.5 9.53 7.5 11.5c0 1.33.67 2 1.5 2 .83 0 1.5-.67 1.5-1.5 0-.83-.67-1.5-1.5-1.5-.17 0-.33.03-.5.08.33-1.17 1.33-2.17 2.5-2.83L11 7.05zM17 7.05c-1.95.98-3.5 2.48-3.5 4.45 0 1.33.67 2 1.5 2 .83 0 1.5-.67 1.5-1.5 0-.83-.67-1.5-1.5-1.5-.17 0-.33.03-.5.08.33-1.17 1.33-2.17 2.5-2.83L17 7.05z"/></svg>
            </div>
            <blockquote class="quote-text">
                Linen is not just a fabric — it is a philosophy of living gently, beautifully, and with purpose.
            </blockquote>
            <div class="line-accent-center" style="margin-top:32px; margin-bottom:16px;"></div>
            <p class="quote-attr">Linea Madison</p>
        </div>
    </section>

    <!-- ===== ABOUT ===== -->
    <section id="about" class="about">
        <div class="container">
            <div class="about-grid">
                <!-- Image Side -->
                <div class="about-image-wrap scroll-reveal">
                    <div class="about-image">
                        <img src="https://z-cdn-media.chatglm.cn/files/84e5295d-4629-4e78-80b4-6e4fbb8cf5ce.png?auth_key=1878771993-474c9e3657e44514b3a608579d1ccb43-0-ac18650f1c767815c1fd1e9e5ac3efe5"
                             alt="About Linea Madison">
                    </div>
                    <div class="about-deco"></div>
                    <div class="about-badge">
                        <div class="about-badge-title">Est.</div>
                        <div class="about-badge-sub">Craftsmanship</div>
                    </div>
                </div>

                <!-- Text Side -->
                <div class="about-text scroll-reveal">
                    <p class="section-eyebrow">Our Story</p>
                    <h2 class="section-title" style="margin-bottom:32px;">Woven with <em>Soul</em></h2>
                    <div class="line-accent" style="margin-bottom:32px;"></div>

                    <p>Linea Madison was born from a deep reverence for linen — the world's oldest and most sustainable textile. We believe that true luxury lies in simplicity, in the gentle touch of natural fibers against the skin, and in garments that grow more beautiful with time.</p>

                    <p>Every piece in our collection is thoughtfully designed to celebrate the female form with relaxed silhouettes, organic textures, and a palette inspired by sun-washed landscapes and Mediterranean earth.</p>

                    <p>From the sourcing of premium European flax to the final stitch, our commitment to quality and sustainability guides every decision we make. This is fashion that feels as good as it looks — honest, intentional, and enduring.</p>

                    <div class="about-values">
                        <div>
                            <div class="about-value-icon">
                                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M11 20A7 7 0 0 1 9.8 6.9C15.5 4.9 17 3.5 19 2c1 2 2 4.5 2 8 0 5.5-4.78 10-10 10Z"/><path d="M2 21c0-3 1.85-5.36 5.08-6C9.5 14.52 12 13 13 12"/></svg>
                            </div>
                            <div class="about-value-label">Natural</div>
                            <div class="about-value-desc">European Flax</div>
                        </div>
                        <div>
                            <div class="about-value-icon">
                                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M19 14c1.49-1.46 3-3.21 3-5.5A5.5 5.5 0 0 0 16.5 3c-1.76 0-3 .5-4.5 2-1.5-1.5-2.74-2-4.5-2A5.5 5.5 0 0 0 2 8.5c0 2.3 1.5 4.05 3 5.5l7 7Z"/></svg>
                            </div>
                            <div class="about-value-label">Ethical</div>
                            <div class="about-value-desc">Fair Practices</div>
                        </div>
                        <div>
                            <div class="about-value-icon">
                                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 12c-2-2.67-4-4-6-4a4 4 0 1 0 0 8c2 0 4-1.33 6-4Zm0 0c2 2.67 4 4 6 4a4 4 0 0 0 0-8c-2 0-4 1.33-6 4Z"/></svg>
                            </div>
                            <div class="about-value-label">Timeless</div>
                            <div class="about-value-desc">Made to Last</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===== CONTACT ===== -->
    <section id="contact" class="contact">
        <div class="contact-bg">
            <img src="https://z-cdn-media.chatglm.cn/files/fd13178c-8df0-427d-b511-283ab1a03be6.png?auth_key=1878771993-335f027ff7394c5dbdbef0148c11dda4-0-0cb53d75496158a21954a1b25d385d1c" alt="">
        </div>

        <div class="contact-content">
            <div class="scroll-reveal">
                <p class="section-eyebrow">Get in Touch</p>
                <h2 class="section-title" style="margin-bottom:24px;">Let's <em>Connect</em></h2>
                <div class="line-accent-center" style="margin-bottom:24px;"></div>
                <p class="contact-desc">
                    We'd love to hear from you. Reach out through any of the channels below — whether it's a question, collaboration, or simply to say hello.
                </p>
            </div>

            <div class="contact-cards scroll-reveal">
                <!-- TikTok -->
                <a href="https://tiktok.com/@lineamadison" target="_blank" rel="noopener noreferrer" class="contact-card">
                    <div class="contact-icon-wrap">
                        <svg viewBox="0 0 24 24"><path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-2.88 2.5 2.89 2.89 0 0 1-2.89-2.89 2.89 2.89 0 0 1 2.89-2.89c.28 0 .54.04.79.1v-3.5a6.37 6.37 0 0 0-.79-.05A6.34 6.34 0 0 0 3.15 15.2a6.34 6.34 0 0 0 6.34 6.34 6.34 6.34 0 0 0 6.34-6.34V8.75a8.18 8.18 0 0 0 4.76 1.52V6.84a4.84 4.84 0 0 1-1-.15z"/></svg>
                    </div>
                    <p class="contact-card-label">TikTok</p>
                    <p class="contact-card-value">@lineamadison</p>
                </a>

                <!-- WhatsApp -->
                <a href="https://wa.me/212660166279" target="_blank" rel="noopener noreferrer" class="contact-card">
                    <div class="contact-icon-wrap">
                        <svg class="stroke-icon" viewBox="0 0 24 24" fill="none" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M7.9 20A9 9 0 1 0 4 16.1L2 22Z"/></svg>
                    </div>
                    <p class="contact-card-label">WhatsApp</p>
                    <p class="contact-card-value">+212 660 166 279</p>
                </a>

                <!-- Email -->
                <a href="mailto:khouloudrad34@gmail.com" class="contact-card">
                    <div class="contact-icon-wrap">
                        <svg class="stroke-icon" viewBox="0 0 24 24" fill="none" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
                    </div>
                    <p class="contact-card-label">Email</p>
                    <p class="contact-card-value">khouloudrad34@gmail.com</p>
                </a>
            </div>
        </div>
    </section>

    <!-- ===== FOOTER ===== -->
    <footer class="footer">
        <div class="container">
            <div class="footer-grid">
                <!-- Brand -->
                <div>
                    <div class="footer-brand-name">LINEA MADISON</div>
                    <div class="footer-brand-line"></div>
                    <p class="footer-brand-desc">
                        Luxury linen clothing crafted for the modern woman. Timeless elegance, natural beauty, sustainable fashion.
                    </p>
                </div>

                <!-- Navigation -->
                <div>
                    <p class="footer-heading">Navigate</p>
                    <div class="footer-nav">
                        <a href="#collection">Collection</a>
                        <a href="#gallery">Gallery</a>
                        <a href="#about">About</a>
                        <a href="#contact">Contact</a>
                    </div>
                </div>

                <!-- Social -->
                <div>
                    <p class="footer-heading">Connect</p>
                    <div class="footer-social">
                        <a href="https://tiktok.com/@lineamadison" target="_blank" rel="noopener noreferrer">
                            <svg viewBox="0 0 24 24" fill="currentColor"><path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-2.88 2.5 2.89 2.89 0 0 1-2.89-2.89 2.89 2.89 0 0 1 2.89-2.89c.28 0 .54.04.79.1v-3.5a6.37 6.37 0 0 0-.79-.05A6.34 6.34 0 0 0 3.15 15.2a6.34 6.34 0 0 0 6.34 6.34 6.34 6.34 0 0 0 6.34-6.34V8.75a8.18 8.18 0 0 0 4.76 1.52V6.84a4.84 4.84 0 0 1-1-.15z"/></svg>
                            @lineamadison
                        </a>
                        <a href="https://wa.me/212660166279" target="_blank" rel="noopener noreferrer">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M7.9 20A9 9 0 1 0 4 16.1L2 22Z"/></svg>
                            +212 660 166 279
                        </a>
                        <a href="mailto:khouloudrad34@gmail.com">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
                            khouloudrad34@gmail.com
                        </a>
                    </div>
                </div>
            </div>

            <div class="footer-divider"></div>

            <div class="footer-bottom">
                <p>© 2025 Linea Madison. All rights reserved.</p>
                <p>Crafted with love & linen</p>
            </div>
        </div>
    </footer>

    <!-- ===== JAVASCRIPT ===== -->
    <script>
        // Navbar scroll effect
        var navbar = document.getElementById('navbar');

        window.addEventListener('scroll', function () {
            if (window.pageYOffset > 80) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Trigger once on load
        if (window.pageYOffset > 80) {
            navbar.classList.add('scrolled');
        }

        // Mobile menu toggle
        var mobileMenuBtn = document.getElementById('mobileMenuBtn');
        var mobileMenu = document.getElementById('mobileMenu');

        mobileMenuBtn.addEventListener('click', function () {
            mobileMenu.classList.toggle('open');
        });

        // Close mobile menu on link click
        var mobileLinks = mobileMenu.querySelectorAll('a');
        for (var i = 0; i < mobileLinks.length; i++) {
            mobileLinks[i].addEventListener('click', function () {
                mobileMenu.classList.remove('open');
            });
        }

        // Scroll reveal
        var scrollElements = document.querySelectorAll('.scroll-reveal');

        var observer = new IntersectionObserver(function (entries) {
            entries.forEach(function (entry) {
                if (entry.isIntersecting) {
                    entry.target.classList.add('revealed');
                    observer.unobserve(entry.target);
                }
            });
        }, {
            threshold: 0.1,
            rootMargin: '0px 0px -60px 0px'
        });

        scrollElements.forEach(function (el) {
            observer.observe(el);
        });

        // Smooth scroll for anchor links
        var anchors = document.querySelectorAll('a[href^="#"]');
        for (var j = 0; j < anchors.length; j++) {
            anchors[j].addEventListener('click', function (e) {
                e.preventDefault();
                var targetId = this.getAttribute('href');
                if (targetId === '#') return;
                var target = document.querySelector(targetId);
                if (target) {
                    var offset = 80;
                    var targetPosition = target.getBoundingClientRect().top + window.pageYOffset - offset;
                    window.scrollTo({
                        top: targetPosition,
                        behavior: 'smooth'
                    });
                }
            });
        }
    </script>

</body>
</html>
