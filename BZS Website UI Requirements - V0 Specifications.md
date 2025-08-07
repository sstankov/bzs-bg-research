# BZS Website UI Requirements - V0 Specifications

## Technology Stack
- **Framework**: React/Next.js
- **Styling**: Tailwind CSS
- **Component Library**: [shadcn/ui](https://ui.shadcn.com/)
- **Design Approach**: Mobile-first responsive design
- **Languages**: Bulgarian (primary) + English

---

## 1. PUBLIC WEBSITE PAGES

### 1.1 Homepage (`/`)

**Purpose**: Entry point showcasing BZS mission, latest news, and key call-to-actions

**Components Needed**:
- `Hero` section with navigation
- `NewsHighlights` carousel/grid
- `QuickActions` card grid
- `EventsPreview` section
- `Footer` with links and contact

**Layout Structure**:
```jsx
<div className="min-h-screen bg-background">
  <Navigation />
  <main>
    <HeroSection />
    <NewsHighlights />
    <QuickActions />
    <EventsPreview />
    <CallToAction />
  </main>
  <Footer />
</div>
```

**Hero Section**:
- Full-width hero with BZS logo and mission statement
- Background: Professional dental imagery with overlay
- Primary CTA: "Станете член" (Become a Member)
- Secondary CTA: "Намерете зъболекар" (Find a Dentist)
- Navigation: Sticky header with language toggle (BG/EN)

**Components**:
- `Button` (primary, secondary variants)
- `Card` for news items
- `Badge` for event dates
- `Separator` between sections

**Mobile Considerations**:
- Hamburger menu for mobile navigation
- Stacked hero content on mobile
- Swipeable news carousel
- Touch-friendly button sizes (min 44px)

---

### 1.2 About BZS (`/about`)

**Purpose**: Comprehensive information about BZS structure, history, and leadership

**Subpages**:
- `/about/history` - Historical timeline
- `/about/structure` - Organizational chart
- `/about/leadership` - Board members and committees
- `/about/regional-colleges` - Regional offices
- `/about/contact` - Contact information and locations

**Main About Page Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <Breadcrumb />
  <h1>За БЗС</h1>
  <Tabs defaultValue="overview">
    <TabsList>
      <TabsTrigger value="overview">Общо</TabsTrigger>
      <TabsTrigger value="structure">Структура</TabsTrigger>
      <TabsTrigger value="history">История</TabsTrigger>
      <TabsTrigger value="leadership">Ръководство</TabsTrigger>
    </TabsList>
    <TabsContent value="overview">
      <AboutOverview />
    </TabsContent>
    {/* Other tabs */}
  </Tabs>
</div>
```

**Leadership Page Components**:
- `Avatar` with fallback initials
- `Card` for each board member
- `Badge` for positions/titles
- `Accordion` for committee details

**Structure Page**:
- Interactive organizational chart
- `TreeView` component or custom hierarchy
- Contact cards for each department

---

### 1.3 Membership & Services (`/membership`)

**Purpose**: Detailed membership packages, benefits, and registration

**Subpages**:
- `/membership/packages` - Different membership tiers
- `/membership/benefits` - Member benefits and discounts
- `/membership/application` - Registration form
- `/membership/renewal` - Renewal process
- `/membership/faq` - Frequently asked questions

**Packages Page Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <h1>Членство и услуги</h1>
  <div className="grid md:grid-cols-3 gap-6 mt-8">
    <PricingCard tier="practicing" />
    <PricingCard tier="student" featured />
    <PricingCard tier="overseas" />
  </div>
  <BenefitsSection />
  <TestimonialsSection />
</div>
```

**Pricing Card Component**:
- `Card` with border highlight for featured
- `Badge` for "Most Popular"
- `Button` for "Изберете план" (Choose Plan)
- `CheckCircle` icons for feature lists
- Annual/monthly toggle with `Switch`

**Benefits Section**:
- Grid of benefit cards with icons
- `Collapsible` sections for detailed descriptions
- Partner logos in `Carousel`

---

### 1.4 Education & Professional Development (`/education`)

**Purpose**: CPD courses, events, certifications, and professional resources

**Subpages**:
- `/education/courses` - Available courses and webinars
- `/education/events` - Conferences and workshops
- `/education/calendar` - Event calendar
- `/education/certificates` - Certification programs
- `/education/research` - Scientific publications

**Courses Page Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <div className="flex flex-col lg:flex-row gap-8">
    <aside className="lg:w-1/4">
      <CourseFilters />
    </aside>
    <main className="lg:w-3/4">
      <CourseGrid />
    </main>
  </div>
</div>
```

**Course Filters Sidebar**:
- `Checkbox` groups for categories
- `Slider` for price range
- `DatePicker` for date filters
- `Select` for sort options
- `Button` to clear all filters

**Course Card Component**:
- Course thumbnail image
- `Badge` for CPD credits
- Star rating with `StarIcon`
- Price display
- "Записване" (Register) button
- Duration and format badges

**Calendar View**:
- `Calendar` component from shadcn/ui
- Event markers on dates
- Popup with event details
- Filter by event type

---

### 1.5 Professional Resources (`/resources`)

**Purpose**: Documents, guidelines, legal resources for dental professionals

**Subpages**:
- `/resources/documents` - Regulatory documents
- `/resources/guidelines` - Clinical guidelines
- `/resources/legal` - Legal templates and advice
- `/resources/practice-management` - Business resources
- `/resources/digital-services` - E-prescription, certificates

**Documents Page Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <SearchAndFilter />
  <div className="grid gap-4 mt-6">
    {documents.map(doc => (
      <DocumentCard key={doc.id} document={doc} />
    ))}
  </div>
  <Pagination />
</div>
```

**Document Card Component**:
- File type icon (`FileText`, `Download` icons)
- Document title and description
- `Badge` for document type (Law, Regulation, etc.)
- Download button with file size
- Last updated date
- Language indicator

**Search and Filter**:
- `Input` with search icon
- `Select` dropdowns for category, year, type
- `DateRangePicker` for date filtering

---

### 1.6 Public Health Information (`/health`)

**Purpose**: Oral health information for citizens and patients

**Subpages**:
- `/health/prevention` - Preventive care guides
- `/health/children` - Pediatric dental health
- `/health/seniors` - Senior dental care
- `/health/emergency` - Emergency dental care
- `/health/insurance` - Dental insurance information

**Health Articles Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <div className="grid lg:grid-cols-4 gap-8">
    <aside className="lg:col-span-1">
      <HealthCategories />
      <RelatedArticles />
    </aside>
    <main className="lg:col-span-3">
      <ArticleContent />
    </main>
  </div>
</div>
```

**Article Card Component**:
- Featured image with overlay
- Category `Badge`
- Reading time estimate
- Author and date
- Social sharing buttons

**Emergency Care Section**:
- Prominent emergency contact cards
- `Alert` component for urgent information
- Step-by-step emergency guides
- Interactive symptom checker

---

### 1.7 Find a Dentist (`/dentist-search`)

**Purpose**: Public directory of registered dentists with search and filter

**Main Search Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <SearchHeader />
  <div className="grid lg:grid-cols-4 gap-6">
    <aside className="lg:col-span-1">
      <SearchFilters />
    </aside>
    <main className="lg:col-span-3">
      <MapView />
      <DentistResults />
    </main>
  </div>
</div>
```

**Search Filters**:
- Location input with autocomplete
- `Checkbox` for specialties
- `Slider` for distance radius
- Language spoken filters
- Insurance accepted filters
- `Switch` for "Accepting new patients"

**Dentist Card Component**:
- Professional photo with `Avatar`
- Name, title, and specialties
- Practice address and contact
- Rating stars
- `Badge` for verification status
- "Покажи повече" (Show More) button
- Quick contact buttons (call, email)

**Map Integration**:
- Interactive map with dentist markers
- Clustered markers for density
- Info popups on marker click
- Current location detection

---

### 1.8 Events & Conferences (`/events`)

**Purpose**: Scientific conferences, workshops, and professional events

**Events Listing Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <EventsHeader />
  <div className="flex flex-col lg:flex-row gap-8">
    <aside className="lg:w-1/4">
      <EventFilters />
    </aside>
    <main className="lg:w-3/4">
      <EventsGrid />
    </main>
  </div>
</div>
```

**Event Card Component**:
- Event banner image
- Date and time with `Calendar` icon
- Location with `MapPin` icon
- `Badge` for event type
- CPD credits available
- Price and registration status
- "Регистрация" (Register) button

**Event Detail Page**:
- Hero section with event details
- `Tabs` for Agenda, Speakers, Location, Registration
- Speaker cards with photos and bios
- Interactive schedule with time slots
- Registration form or external link

---

### 1.9 Publications & Media (`/publications`)

**Purpose**: Dentamedica newspaper, journals, research papers

**Subpages**:
- `/publications/dentamedica` - Monthly newspaper
- `/publications/journal` - Scientific journal
- `/publications/research` - Research papers
- `/publications/archive` - Historical publications

**Publications Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <div className="grid lg:grid-cols-3 gap-8">
    <main className="lg:col-span-2">
      <FeaturedPublication />
      <RecentPublications />
    </main>
    <aside className="lg:col-span-1">
      <ArchiveSearch />
      <Categories />
    </aside>
  </div>
</div>
```

**Publication Card**:
- Cover image thumbnail
- Title and issue details
- Publication date
- `Badge` for publication type
- Download/read buttons
- Page count and file size

**Archive Search**:
- `Input` for search terms
- `Select` for year and issue
- `DateRangePicker` for date range
- Category filters

---

### 1.10 News & Advocacy (`/news`)

**Purpose**: Press releases, policy updates, advocacy campaigns

**News Listing Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <div className="grid lg:grid-cols-4 gap-8">
    <main className="lg:col-span-3">
      <FeaturedNews />
      <NewsGrid />
    </main>
    <aside className="lg:col-span-1">
      <NewsCategories />
      <NewsletterSignup />
    </aside>
  </div>
</div>
```

**News Article Card**:
- Featured image with overlay
- Category `Badge`
- Headline and excerpt
- Author and publish date
- Read time estimate
- Social sharing icons

**Featured News**:
- Large hero image
- Overlay text with headline
- "Прочети повече" (Read More) button
- Category navigation

---

## 2. MEMBER PORTAL/DASHBOARD

### 2.1 Member Dashboard (`/dashboard`)

**Purpose**: Personalized member overview with key information and quick actions

**Dashboard Layout**:
```jsx
<div className="min-h-screen bg-background">
  <DashboardHeader />
  <div className="container mx-auto px-4 py-8">
    <div className="grid lg:grid-cols-4 gap-6">
      <main className="lg:col-span-3">
        <WelcomeSection />
        <QuickStats />
        <RecentActivity />
        <UpcomingEvents />
      </main>
      <aside className="lg:col-span-1">
        <MembershipCard />
        <QuickActions />
        <Notifications />
      </aside>
    </div>
  </div>
</div>
```

**Quick Stats Cards**:
- CPD Credits earned/required with `Progress` bar
- Membership status with renewal date
- Registered events count
- Documents downloaded this month

**Membership Status Card**:
- Member photo and name
- Membership tier with `Badge`
- Renewal date with countdown
- Digital membership card
- QR code for verification

**Quick Actions Panel**:
- "Обнови членството" (Renew Membership)
- "Регистрирай събитие" (Register Event)
- "Изтегли сертификат" (Download Certificate)
- "Актуализирай профил" (Update Profile)

---

### 2.2 Profile Management (`/dashboard/profile`)

**Purpose**: Member personal and professional information management

**Profile Form Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <Tabs defaultValue="personal">
    <TabsList>
      <TabsTrigger value="personal">Лични данни</TabsTrigger>
      <TabsTrigger value="professional">Професионални</TabsTrigger>
      <TabsTrigger value="practice">Практика</TabsTrigger>
      <TabsTrigger value="preferences">Настройки</TabsTrigger>
    </TabsList>
    <TabsContent value="personal">
      <PersonalInfoForm />
    </TabsContent>
    {/* Other tabs */}
  </Tabs>
</div>
```

**Form Components Needed**:
- `Input` fields for text data
- `Textarea` for descriptions
- `Select` for dropdowns (specialty, region)
- `Checkbox` for multiple selections
- `RadioGroup` for single selections
- `DatePicker` for dates
- `Avatar` upload component

**Professional Info Section**:
- License number and verification
- Specialties with `Badge` display
- Education history
- Professional certifications
- Work experience timeline

---

### 2.3 CPD & Education Portal (`/dashboard/education`)

**Purpose**: Continuing Professional Development tracking and course access

**Education Dashboard Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <div className="grid lg:grid-cols-3 gap-8">
    <main className="lg:col-span-2">
      <CPDProgress />
      <MyCourses />
      <AvailableCourses />
    </main>
    <aside className="lg:col-span-1">
      <CPDSummary />
      <Certificates />
      <Recommendations />
    </aside>
  </div>
</div>
```

**CPD Progress Component**:
- Circular progress indicator
- Credits earned vs required
- Time remaining to deadline
- `Progress` bars for different categories

**Course Card in Portal**:
- Course thumbnail and title
- Progress bar if enrolled
- Completion status with checkmark
- Certificate download if completed
- "Продължи" (Continue) or "Започни" (Start) button

**Certificates Section**:
- Downloadable certificate list
- PDF preview capability
- Share certificate functionality
- Print-ready formatting

---

### 2.4 Membership & Payments (`/dashboard/membership`)

**Purpose**: Membership management, payments, and renewal

**Membership Page Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <MembershipOverview />
  <div className="grid lg:grid-cols-2 gap-8 mt-8">
    <PaymentHistory />
    <MembershipActions />
  </div>
  <BenefitsUsage />
</div>
```

**Payment History Table**:
- `Table` with payment records
- Date, amount, description, status
- `Badge` for payment status
- Download receipt buttons
- Filter and search capabilities

**Renewal Section**:
- Current plan details
- Renewal options with pricing
- Auto-renewal toggle with `Switch`
- Payment method selection
- Confirmation dialog

---

### 2.5 Events & Registration (`/dashboard/events`)

**Purpose**: Event registration management and history

**Events Management Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <Tabs defaultValue="registered">
    <TabsList>
      <TabsTrigger value="registered">Регистрирани</TabsTrigger>
      <TabsTrigger value="attended">Посетени</TabsTrigger>
      <TabsTrigger value="available">Налични</TabsTrigger>
    </TabsList>
    <TabsContent value="registered">
      <RegisteredEvents />
    </TabsContent>
    {/* Other tabs */}
  </Tabs>
</div>
```

**Event Registration Card**:
- Event details and date
- Registration status with `Badge`
- QR code for check-in
- Calendar integration button
- Cancellation option if allowed

---

### 2.6 Downloads & Resources (`/dashboard/resources`)

**Purpose**: Access to member-only documents and resources

**Resources Layout**:
```jsx
<div className="container mx-auto px-4 py-8">
  <div className="flex flex-col lg:flex-row gap-8">
    <aside className="lg:w-1/4">
      <ResourceFilters />
    </aside>
    <main className="lg:w-3/4">
      <ResourceGrid />
    </main>
  </div>
</div>
```

**Resource Card**:
- Document icon based on file type
- Title and description
- `Badge` for member-only content
- Download count and file size
- Favorite/bookmark option
- Last updated date

---

## 3. ADMINISTRATIVE INTERFACE

### 3.1 Admin Dashboard (`/admin`)

**Purpose**: Administrative overview and quick access to management functions

**Admin Layout**:
```jsx
<div className="min-h-screen bg-background">
  <AdminSidebar />
  <div className="lg:pl-64">
    <AdminHeader />
    <main className="p-6">
      <AdminOverview />
      <QuickActions />
      <RecentActivity />
    </main>
  </div>
</div>
```

**Admin Overview Cards**:
- Total members with growth indicator
- Active events and registrations
- Recent payments and revenue
- Support tickets pending
- Website analytics summary

---

### 3.2 Member Management (`/admin/members`)

**Purpose**: Comprehensive member database management

**Member Management Layout**:
```jsx
<div className="p-6">
  <div className="flex justify-between items-center mb-6">
    <h1>Управление на членове</h1>
    <Button>Добави член</Button>
  </div>
  <MemberFilters />
  <MemberTable />
  <Pagination />
</div>
```

**Member Table Columns**:
- Member photo and name
- Membership type and status
- Registration date
- Last activity
- Payment status
- Actions dropdown

---

### 3.3 Content Management (`/admin/content`)

**Purpose**: Website content management system

**Content CMS Layout**:
```jsx
<div className="p-6">
  <Tabs defaultValue="pages">
    <TabsList>
      <TabsTrigger value="pages">Страници</TabsTrigger>
      <TabsTrigger value="news">Новини</TabsTrigger>
      <TabsTrigger value="events">Събития</TabsTrigger>
      <TabsTrigger value="media">Медия</TabsTrigger>
    </TabsList>
    <TabsContent value="pages">
      <PageManager />
    </TabsContent>
    {/* Other tabs */}
  </Tabs>
</div>
```

---

### 3.4 Event Management (`/admin/events`)

**Purpose**: Create and manage events, registrations, and attendance

**Event Management Features**:
- Event creation wizard
- Registration management
- Attendance tracking
- Certificate generation
- Revenue reporting

---

### 3.5 Financial Reports (`/admin/reports`)

**Purpose**: Financial reporting and analytics

**Reports Dashboard**:
- Revenue charts with `Chart` components
- Membership statistics
- Event performance metrics
- Export functionality

---

## 4. SHARED COMPONENTS & PATTERNS

### 4.1 Navigation Components

**Main Navigation**:
```jsx
<nav className="bg-white shadow-sm border-b">
  <div className="container mx-auto px-4">
    <div className="flex items-center justify-between h-16">
      <Logo />
      <NavigationMenu />
      <UserActions />
    </div>
  </div>
</nav>
```

**Mobile Navigation**:
- `Sheet` component for mobile menu
- Collapsible menu sections
- Touch-friendly spacing

### 4.2 Form Components

**Standard Form Pattern**:
```jsx
<form className="space-y-6">
  <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
    <FormField>
      <Label>Име</Label>
      <Input placeholder="Въведете име" />
      <FormMessage />
    </FormField>
  </div>
  <div className="flex justify-end space-x-4">
    <Button variant="outline">Отказ</Button>
    <Button type="submit">Запази</Button>
  </div>
</form>
```

### 4.3 Loading States

**Loading Patterns**:
- `Skeleton` components for content loading
- `Spinner` for button loading states
- `Progress` bars for file uploads

### 4.4 Error Handling

**Error Components**:
- `Alert` for form validation errors
- `Toast` for success/error messages
- Error boundary pages

### 4.5 Search Patterns

**Universal Search Component**:
```jsx
<div className="relative">
  <SearchIcon className="absolute left-3 top-3" />
  <Input 
    placeholder="Търсене..." 
    className="pl-10"
  />
  <SearchResults />
</div>
```

---

## 5. RESPONSIVE DESIGN SPECIFICATIONS

### 5.1 Breakpoints (Tailwind CSS)
- `sm`: 640px
- `md`: 768px  
- `lg`: 1024px
- `xl`: 1280px
- `2xl`: 1536px

### 5.2 Mobile-First Approach

**Navigation**:
- Mobile: Hamburger menu with `Sheet`
- Desktop: Horizontal navigation with dropdowns

**Content Grid**:
- Mobile: Single column layout
- Tablet: 2-column grid
- Desktop: 3-4 column grid

**Forms**:
- Mobile: Stacked form fields
- Desktop: Multi-column layout where appropriate

### 5.3 Touch Targets
- Minimum 44px for interactive elements
- Adequate spacing between clickable items
- Swipe gestures for carousels

---

## 6. ACCESSIBILITY CONSIDERATIONS

### 6.1 WCAG 2.1 AA Compliance
- Semantic HTML structure
- Proper heading hierarchy
- Alt text for images
- Keyboard navigation support
- Screen reader compatibility

### 6.2 shadcn/ui Accessibility
- Built-in accessibility features
- ARIA attributes
- Focus management
- High contrast support

---

## 7. PERFORMANCE CONSIDERATIONS

### 7.1 Image Optimization
- Next.js Image component
- WebP format with fallbacks
- Lazy loading for images below fold

### 7.2 Code Splitting
- Route-based code splitting
- Dynamic imports for heavy components
- Progressive loading for dashboard components

---

This comprehensive specification provides the foundation for creating high-fidelity prototypes using V0 with React/Next.js, Tailwind CSS, and shadcn/ui components, following mobile-first responsive design principles.