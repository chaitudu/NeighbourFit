🏘️ NeighbourFit — Smart Neighborhood Lifestyle Matcher
NeighbourFit is a full-stack web application built to solve the neighborhood-lifestyle matching problem. It leverages real-world data, algorithmic matching, and modern web technologies to help users find neighborhoods that align with their lifestyle preferences.

📌 Project Overview
This project is part of a two-week assignment focused on solving real-world problems using systematic research, data-driven analysis, and full-stack engineering.

Key Focus Areas:

Problem analysis through research and hypothesis testing

Building a robust matching algorithm

Handling real-world data acquisition and inconsistencies

Deploying a fully functional application with admin tools

🚀 Features
🧠 Matching Algorithm
Lifestyle-to-neighborhood mapping

Multi-criteria scoring based on user input

Real-time filtering and result suggestions

📊 Real-World Data Handling
Integration with open data sources (e.g., public APIs, CSVs)

Data normalization and edge case handling

Live updates on neighborhood statistics

🔐 Authentication
Email/password, Google OAuth, and OTP login (via Supabase)

Role-based access (User & Admin)

Session management and protected routes

🧰 Admin Dashboard
Manage user data and submissions

View site analytics and neighborhood performance

Moderate contact messages and feedback

🌐 Responsive UI
Modern design using Tailwind CSS

Animations with Framer Motion

Mobile-first layout with SEO optimization

🛠️ Tech Stack
Layer	Technology
Frontend	React 18, TypeScript, Vite, Tailwind CSS
Backend	Supabase (PostgreSQL), Supabase Auth
Animations	Framer Motion, AOS
State Mgmt	React Context API
Routing	React Router DOM
Notifications	React Hot Toast
Deployment	Vercel / Firebase Hosting

🧪 Matching Algorithm Design
Weighted scoring model based on:

Safety

Commute times

Amenities

Green spaces

Cost of living

Rule-based logic with threshold filters

Data-driven adjustments based on user feedback

🧬 Database Schema Highlights
user_profiles
Stores user data, roles (admin/user), and timestamps

RLS enforced for user-specific access

contact_messages
Captures inquiries with status tracking (new, read, replied)

blog_posts
CMS-style blog table for admin content management

(SQL schemas included in /db/schema.sql)

📈 Research & Problem-Solving Approach
🧩 Problem Definition
Users struggle to identify neighborhoods that match their daily needs and preferences.

🔍 Methodology
User interviews + online surveys

Competitive analysis of existing platforms (e.g., Niche, Zillow)

Identified lack of personalization in current solutions

💡 Hypotheses
Users prioritize safety, commute, and community vibe

Personalization boosts engagement and satisfaction

🔬 Data-Driven Testing
Built mock datasets with public data

Validated algorithm output with known benchmarks

🚧 Real-World Constraints
🕒 2-week timeline

💰 Zero budget — only free APIs and tools

📉 Limited neighborhood data — handled via creative scraping and mocks

📦 Getting Started
bash
Copy
Edit
# 1. Clone the repository
git clone https://github.com/chaitudu/NeighbourFit
cd NeighbourFit

# 2. Install dependencies
npm install

# 3. Set up environment variables
cp .env.example .env  # Then fill in Supabase credentials

# 4. Run development server
npm run dev
🧪 Testing & Validation
Manual test cases for edge inputs (e.g., unknown location, empty preferences)

Integration test between form → result → dashboard

Performance checks with mock data

🌍 Deployment
Deployed to:

🔗 https://neighbourfit.vercel.app (or Firebase, update if needed)

🧠 Reflection & Learnings
Systematically broke down the problem from user needs to backend logic

Faced challenges with real-world data inconsistency and solved via fallback heuristics

Future work: ML-based scoring, sentiment analysis on community feedback

📝 License
This project is licensed under the MIT License. See LICENSE for details.

🤝 Contributing
Fork this repo

Create a feature branch (git checkout -b feature-name)

Commit your changes and push

Open a Pull Request

📬 Contact
For questions, feedback, or collaboration:
📧 chaitanyamodalavalsa@gmail.com
