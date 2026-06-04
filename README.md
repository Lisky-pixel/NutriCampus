# nutricampus
# NutriCampus – Personalized Meal Recommendation & Nutrition Tracking for University Students

NutriCampus is a fullstack web and mobile nutrition platform designed to improve the dietary habits of university students in Kigali, Rwanda. The platform addresses the trade-off between affordability and nutrition that most campus students face daily, providing personalized, budget-aware meal guidance built around a localized East African food database.

Rather than adapting a global app to an African context, NutriCampus is built from the ground up for the Rwandan student experience — local foods, local prices in RWF, low-bandwidth mobile conditions, and realistic student budgets.

---

## Project Description

University students in Sub-Saharan Africa face a well-documented tension between cost and nutritional quality. At ALU in Kigali, most students rely on informal campus vendors with no nutritional transparency. Existing global nutrition apps fail this population in three key ways:

No localized food database covering East African or Rwandan meals
Subscription pricing and data-heavy interfaces unsuitable for student budgets and mobile networks
No mechanism to match meal recommendations to a student's actual daily nutritional gap

NutriCampus addresses these issues by prioritizing:

**Personalized recommendations** driven by a content-based filtering engine
**A localized food database** with Rwandan and East African meals priced in RWF
**Macro and calorie tracking** against individually set daily targets
**Budget-aware filtering** so every recommendation stays within what a student can spend
**A weekly gap analysis dashboard** that makes nutritional deficits visible and actionable

This project is developed as a **final year capstone project at the African Leadership University**, with emphasis on system design, recommendation algorithms, and localization for the African mobile context. The platform is intended to scale beyond the academic phase into a deployable campus tool.

---

## Designs

### React UI Prototype

The interactive prototype demonstrates the full system behavior across all six screens, built as a functional React component with a complete design system.

**Design system:**
Fonts: Syne (headings) + DM Sans (body)
Primary: #3B6D11 earthy green / Light: #EAF3DE
Accent: #BA7517 amber / Light: #FAEEDA
Warm: #D85A30 terracotta / Light: #FAECE7
Mobile-first, 390px max-width, flat design

**Screens built:**

1. **Onboarding (3 steps)** — Name / age / weight → Health goal selection → Dietary restrictions and budget slider
2. **Home Dashboard** — Greeting, SVG nutrition ring, macro progress bars, streak and water intake cards, recommended meals grid
3. **Meal Finder** — Category filter tabs (all / breakfast / lunch / dinner / snack), 2-column meal card grid, tap-to-open detail sheet with macro breakdown and "Log This Meal" CTA
4. **Today's Log** — Timeline grouped by meal type, daily calorie summary, logged items with per-item macro display
5. **Weekly Progress** — Stats cards, calorie bar chart (met / below color-coded), macro split bars, nutritional gap alerts
6. **Profile** — Avatar, health stats grid, goal and restriction settings

**Local food data used in prototype:**
Isombe + Rice, Beans & Chapati, Ugali + Sukuma Wiki, Matoke + Beef Stew, Mandazi + Chai, Ibijumba + Veggies, Samosa + Mango Juice, Rice + Fish Stew. All prices in RWF.

---

## System Diagrams

The following diagrams guide the design and implementation of the system:

### 1. System Architecture

Student (Mobile / Web App)
          ↓
   REST API — Node.js + Express
          ↓                  ↓
  PostgreSQL DB      Recommendation Engine
          ↓                  ↓
   FoodItem DB       Content-based Filter
          ↓
USDA FoodData Central API (external)

### 2. Entity Relationship Diagram (ERD)

Core entities and relationships:

User — health profile, goal, daily budget
DietaryRestriction — linked to User
FoodItem — nutritional data, category, price in RWF, source (USDA or local)
MealLog — links User to FoodItem with serving size and meal type
NutritionalProfile — daily macro targets per user
Recommendation — scored meal suggestions generated per session

### 3. Recommendation Engine Logic

Compute daily nutritional deficit: RDA_target − sum(logged_meal_nutrients)
Score each available food item against the deficit using cosine similarity or weighted gap scoring
Filter results by dietary restrictions and student daily budget
Return a ranked list with a match percentage score
Cold start handling for new users: derive estimated RDA from health profile (goal + age + weight)

### 4. UML Diagrams

**Use Case:** Student logs meal / views recommendations / updates profile; Admin manages food database
**Sequence:** Recommendation request flow — student opens app → API call → engine scores meals → ranked list returned
**Class Diagram:** User, MealLog, FoodItem, NutritionalProfile, Recommendation, DailyTarget

(Diagrams are included in the project report and design documentation.)

---

## Deployment Plan (Conceptual)

At the current stage, NutriCampus focuses on **design, prototyping, and system modelling** rather than full production deployment.

### Planned Architecture

**Web Frontend:** React
**Mobile:** React Native or Flutter (cross-platform, shared business logic)
**Backend:** Node.js + Express — REST API
**Database:** MongoDB with Prisma or Sequelize ORM
**Authentication:** JWT (stateless, mobile-friendly)
**Nutritional Data:** USDA FoodData Central API + manually entered local food entries
**Hosting:**
Frontend → Vercel (free tier)
Backend → Render (free tier)

Production deployment, a collaborative filtering upgrade, and mobile app store release are planned as future work beyond the capstone timeline.

---

## Video Demo

🎥 **Video Demo:** (add link here)

The demo will showcase:

Student onboarding and health profile setup
Meal recommendation flow driven by daily nutritional deficit
Meal logging and macro tracking
Weekly progress dashboard and gap analysis
Local Rwandan food database in action

---

## Current Project Phase

✅ Problem analysis and system requirements defined  
✅ UX/UI design and interactive React prototype  
✅ System architecture, ERD, and algorithm design  
🔄 Backend API implementation (Node.js + Express + MongoDB) — planned  
🔄 Recommendation engine build — planned  
🔄 Mobile app development — planned  
🔄 Pilot evaluation with ALU students — planned  

---

## Key Technologies

### Design & Prototyping
React (interactive UI prototype), Figma

### Web Frontend
React

### Mobile
React Native / Flutter

### Backend & Infrastructure
Node.js + Express  
MongoDB
Prisma or Sequelize (ORM)  
JWT (authentication)

### External APIs
USDA FoodData Central API (nutritional data)

### Hosting
Vercel (frontend) · Render (backend)

### Testing
Jest (unit) · Postman (API)

---

## Author

**[Oluchi Rejoice Nduka-aku]**  
Final Year Student, African Leadership University  
BSc. Software Engineering  
Project: NutriCampus