# Anamaya Health Platform - Design Guidelines

## Design Approach

**Reference-Based Approach**: Drawing inspiration from trusted healthcare platforms like Practo, Zocdoc, and Apollo 24/7, adapted for rural and semi-urban Indian users with emphasis on simplicity and trustworthiness.

**Core Principles**:
- Trust & Credibility: Clean, professional layouts that inspire confidence
- Accessibility First: Large touch targets, clear labels, high contrast for users with varying digital literacy
- Cultural Sensitivity: Design patterns familiar to Indian users, multilingual considerations
- Mobile-Optimized: 60%+ users will access via mobile devices

## Typography System

**Font Family**: Poppins (via Google Fonts CDN) - chosen for excellent readability in Latin and Devanagari scripts

**Hierarchy**:
- Hero Headlines: text-4xl to text-6xl, font-semibold (600)
- Section Headers: text-3xl to text-4xl, font-semibold (600)
- Subsection Headers: text-xl to text-2xl, font-medium (500)
- Body Text: text-base to text-lg, font-normal (400)
- Supporting Text: text-sm, font-normal (400)
- Buttons/CTAs: text-base to text-lg, font-medium (500)

## Layout System

**Spacing Primitives**: Tailwind units of 4, 6, 8, 12, 16, 20 for consistent vertical rhythm
- Component padding: p-6, p-8
- Section spacing: py-12, py-16, py-20
- Element gaps: gap-4, gap-6, gap-8
- Card spacing: p-6 to p-8

**Container Widths**:
- Full sections: max-w-7xl mx-auto
- Content areas: max-w-6xl mx-auto
- Forms: max-w-2xl mx-auto
- Text content: max-w-3xl mx-auto

**Grid Systems**:
- Doctor cards: grid-cols-1 md:grid-cols-2 lg:grid-cols-3
- Feature highlights: grid-cols-1 md:grid-cols-2
- Subscription plans: grid-cols-1 md:grid-cols-3
- Mobile-first: All grids collapse to single column on mobile

## Component Library

### Navigation Bar
- Sticky header with shadow on scroll
- Logo left-aligned, language selector and login/signup right-aligned
- Mobile: Hamburger menu with slide-in drawer
- Height: h-16 to h-20 with proper padding
- Include: Logo, Main nav links (Home, Services, Doctors, About), Language dropdown, Login/Signup buttons

### Homepage Structure

**Hero Section** (80vh on desktop, auto-height mobile):
- Full-width background with healthcare imagery (doctors with patients, modern clinic, medical care)
- Overlay with semi-transparent gradient for text readability
- Centered content: Large headline, supporting text, primary CTA ("Find a Doctor" / "Get Started")
- Trust indicators below CTA: "10,000+ Patients Served" or "500+ Qualified Doctors"

**About Section**:
- Two-column layout: Left (text content), Right (supportive image or infographic)
- Include mission statement, key values, and trust badges
- Icon-based feature highlights: 24/7 Support, Multi-language, Free Service

**Services Grid**:
- Three-column cards showcasing: AI Diagnosis, Find Doctors, Health Records
- Each card: Icon, title, description, "Learn More" link
- Rounded corners, subtle shadow, hover lift effect

**How It Works Section**:
- Numbered step cards (1-2-3) in horizontal layout
- Large numbers, clear descriptions
- Progress line connecting steps

**Footer**:
- Multi-column: Quick Links, Services, Contact Info, Social Media
- Language selector repeated
- Disclaimer about AI diagnosis being preliminary
- Copyright and terms

### Add Patient Form
- Single-column form layout with clear section headers
- Grouped fields: Personal Details, Contact Information, Medical History
- Form sections with light background panels for visual separation
- Field layout: Label above input, helper text below
- Input types: Text fields, dropdowns, date pickers, checkboxes, textarea for medical history
- Large, accessible form controls (h-12 for inputs)
- Clear validation feedback with color-coded messages
- Submit button prominent at bottom: Full-width on mobile, fixed width on desktop
- Multi-step progress indicator if form is split into steps

### AI Diagnosis Page
- Two-panel layout: Left (symptom input), Right (results/doctor suggestions)
- Symptom input: Large textarea with character count, dropdown for severity, checkbox for urgent care
- "Analyze Symptoms" button prominent and clear
- Results area: AI-generated assessment card with disclaimer banner at top
- Doctor recommendations: Card grid with photos, specialties, ratings, distance, availability
- Each doctor card: Photo, name, specialty, experience, location, "Book Consultation" button
- Filter sidebar: Specialty, distance, availability (collapsible on mobile)

### Subscription/Membership Page
- Hero section explaining free healthcare access
- Three-column plan cards (Basic, Standard, Premium) - all free with different feature sets
- Each card: Plan name, feature list with checkmarks, medicine reminder details, scheme information
- Government health schemes section: Ayushman Bharat, state schemes with eligibility info
- Medicine reminder feature showcase with phone mockup showing notifications
- No payment gateway - "Join Free" CTAs throughout

### Language Flexibility
- Persistent language selector in header and footer
- Flag icons + language names for clarity
- Support for: English, Hindi, and 2-3 regional languages
- All UI text, form labels, and static content translatable
- RTL support considerations for future expansion
- Default language detection based on browser settings

### General UI Elements

**Buttons**:
- Primary: Large (h-12), rounded-lg, with icon support
- Secondary: Outlined variant
- Disabled states clearly indicated
- Minimum width for consistency

**Cards**:
- Rounded corners (rounded-lg to rounded-xl)
- Subtle shadow (shadow-md)
- Padding p-6 to p-8
- Hover state: Slight lift (transform translateY)

**Form Inputs**:
- Height h-12, rounded-lg
- Clear focus states with border changes
- Error states with red borders and messages
- Success states with green checkmarks

**Icons**: Use Heroicons via CDN for consistent iconography throughout

## Images

**Required Images**:

1. **Homepage Hero**: Professional healthcare scene - doctors consulting with patients in modern clinic, conveying trust and care (full-width, 80vh)

2. **About Section**: Team of diverse doctors or healthcare facility exterior (side image, ~40% width)

3. **Services Icons**: Medical diagnostics, stethoscope, health records (icon-sized, used in cards)

4. **Doctor Profile Photos**: Professional headshots for doctor cards (square, 200x200px minimum)

5. **App Mockup**: Phone showing medicine reminder notifications (for subscription page)

6. **Trust Badges**: Medical certification logos, government scheme emblems

## Accessibility & Trust Elements

- High contrast text for readability in bright outdoor conditions
- Large minimum font size (16px base) for older users
- Touch targets minimum 44x44px
- Medical disclaimer text on AI diagnosis
- Privacy notice on patient form
- Verified doctor badges
- Patient testimonials with photos
- Certification badges in footer

## Animation Guidelines

**Minimal, Purposeful Animations**:
- Page transitions: Simple fade-in (200ms)
- Card hover: Subtle lift (transform translateY(-4px), 200ms)
- Form validation: Shake animation for errors
- Loading states: Simple spinner for AI diagnosis
- NO complex scroll animations or parallax effects
- NO auto-playing carousels

## Mobile-Specific Considerations

- Bottom navigation bar for primary actions on mobile
- Collapsible sections to reduce scrolling
- Sticky CTA buttons on forms
- Tap-friendly spacing between interactive elements
- Optimized images for 3G connections
- Offline-first approach where possible

This design system prioritizes clarity, trust, and accessibility for rural and semi-urban users while maintaining a modern, professional healthcare aesthetic.