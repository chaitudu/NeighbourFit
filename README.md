# Modern Company Website

A comprehensive, modern company website built with React, TypeScript, and Supabase. Features real-time functionality, authentication, admin dashboard, and beautiful animations.

## 🚀 Features

### 🎨 Frontend
- **Modern Design**: Clean, professional UI with smooth animations using Framer Motion
- **Responsive Layout**: Mobile-first design with Tailwind CSS
- **Interactive Elements**: Hover effects, micro-interactions, and smooth transitions
- **SEO Optimized**: Meta tags, structured data, and performance optimized

### 🔐 Authentication
- **Multiple Login Methods**: Email/password, Google OAuth, Phone/OTP
- **Role-based Access**: User and admin roles with protected routes
- **Session Management**: Secure authentication with Supabase Auth

### 💬 Real-time Features
- **Live Chat Widget**: Custom chat interface with bot responses
- **Real-time Contact Forms**: Instant form submissions with validation
- **Live Notifications**: Toast notifications for user feedback
- **Real-time Updates**: Database changes reflected instantly

### 🛠️ Admin Dashboard
- **Content Management**: Manage blog posts, services, and team members
- **Message Management**: View and respond to contact messages
- **User Management**: Monitor user activity and manage accounts
- **Analytics**: View website statistics and performance metrics

### 📱 Pages
- **Home**: Hero section, features, testimonials, and CTA
- **About**: Company story, values, team, and statistics
- **Services**: Service offerings with pricing and features
- **Blog**: Dynamic blog with search, filtering, and categories
- **Contact**: Contact form, map integration, and multiple contact methods
- **Admin Dashboard**: Comprehensive admin panel for content management

## 🛠️ Tech Stack

- **Frontend**: React 18, TypeScript, Vite
- **Styling**: Tailwind CSS
- **Animations**: Framer Motion, AOS
- **Authentication**: Supabase Auth
- **Database**: Supabase (PostgreSQL)
- **State Management**: React Context
- **Routing**: React Router DOM
- **Notifications**: React Hot Toast
- **Icons**: Lucide React

## 📦 Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd modern-company-website
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Fill in your Supabase credentials and other API keys in the `.env` file.

4. **Set up Supabase**
   - Create a new Supabase project
   - Run the database migrations (see Database Setup section)
   - Configure authentication providers

5. **Start the development server**
   ```bash
   npm run dev
   ```

## 🗄️ Database Setup

Create the following tables in your Supabase database:

### User Profiles Table
```sql
create table user_profiles (
  id uuid references auth.users on delete cascade primary key,
  email text unique not null,
  full_name text,
  role text default 'user' check (role in ('user', 'admin')),
  created_at timestamp with time zone default timezone('utc'::text, now()) not null,
  updated_at timestamp with time zone default timezone('utc'::text, now()) not null
);

-- Enable RLS
alter table user_profiles enable row level security;

-- Create policies
create policy "Users can view own profile" on user_profiles
  for select using (auth.uid() = id);

create policy "Users can update own profile" on user_profiles
  for update using (auth.uid() = id);
```

### Contact Messages Table
```sql
create table contact_messages (
  id uuid default gen_random_uuid() primary key,
  name text not null,
  email text not null,
  subject text not null,
  message text not null,
  status text default 'new' check (status in ('new', 'read', 'replied')),
  created_at timestamp with time zone default timezone('utc'::text, now()) not null
);

-- Enable RLS
alter table contact_messages enable row level security;

-- Create policies (admin only)
create policy "Admins can manage messages" on contact_messages
  for all using (
    exists (
      select 1 from user_profiles
      where user_profiles.id = auth.uid()
      and user_profiles.role = 'admin'
    )
  );
```

### Blog Posts Table
```sql
create table blog_posts (
  id uuid default gen_random_uuid() primary key,
  title text not null,
  excerpt text not null,
  content text not null,
  author text not null,
  published_date timestamp with time zone default timezone('utc'::text, now()) not null,
  category text not null,
  image_url text,
  read_time integer default 5,
  views integer default 0,
  created_at timestamp with time zone default timezone('utc'::text, now()) not null,
  updated_at timestamp with time zone default timezone('utc'::text, now()) not null
);

-- Enable RLS
alter table blog_posts enable row level security;

-- Create policies
create policy "Anyone can view published posts" on blog_posts
  for select using (true);

create policy "Admins can manage posts" on blog_posts
  for all using (
    exists (
      select 1 from user_profiles
      where user_profiles.id = auth.uid()
      and user_profiles.role = 'admin'
    )
  );
```

## 🔧 Configuration

### Supabase Setup
1. Create a new project at [supabase.com](https://supabase.com)
2. Get your project URL and anon key from Settings > API
3. Configure authentication providers in Authentication > Settings
4. Set up the database tables using the SQL above

### Google OAuth Setup
1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create a new project or select existing
3. Enable Google+ API
4. Create OAuth 2.0 credentials
5. Add your domain to authorized origins
6. Configure in Supabase Authentication settings

### Email Configuration (Optional)
For contact form emails, you can integrate with:
- SendGrid
- Nodemailer with Gmail SMTP
- EmailJS for client-side email sending

## 🚀 Deployment

### Vercel (Recommended)
1. Push your code to GitHub
2. Connect your repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy automatically on push

### Netlify
1. Build the project: `npm run build`
2. Deploy the `dist` folder to Netlify
3. Configure environment variables
4. Set up continuous deployment

### Firebase Hosting
1. Install Firebase CLI: `npm install -g firebase-tools`
2. Initialize Firebase: `firebase init hosting`
3. Build and deploy: `npm run build && firebase deploy`

## 📊 Analytics Integration

### Google Analytics
Add your GA4 measurement ID to the environment variables and include the tracking script.

### Hotjar
Add your Hotjar site ID to track user behavior and heatmaps.

## 🔒 Security Features

- **Row Level Security**: Database access controlled by user roles
- **Input Validation**: Client and server-side validation
- **XSS Protection**: Sanitized user inputs
- **CSRF Protection**: Secure form submissions
- **Rate Limiting**: API endpoint protection

## 🎨 Customization

### Styling
- Modify `tailwind.config.js` for custom colors and themes
- Update component styles in individual files
- Add custom CSS in `src/index.css`

### Content
- Update company information in components
- Modify service offerings in Services page
- Customize blog categories and content
- Update contact information and social links

### Features
- Add new pages by creating components and routes
- Extend the admin dashboard with new features
- Integrate additional third-party services
- Add more authentication providers

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📞 Support

For support and questions:
- Email: support@techcorp.com
- Documentation: [Link to docs]
- Issues: [GitHub Issues]

## 🔄 Updates

This project is actively maintained. Check the changelog for recent updates and new features.