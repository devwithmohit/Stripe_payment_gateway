# Stripe Subscriptions

A full-stack Next.js subscription payment system with Stripe integration, featuring user authentication via Kinde, tiered pricing (Free/Premium), MongoDB database, and dark mode support.

## Features

- 🔐 **Authentication**: Seamless user authentication with Kinde OAuth
- 💳 **Stripe Integration**: Complete payment processing and subscription management
- 💰 **Tiered Pricing**: Support for Free and Premium subscription tiers
- 📅 **Subscription Management**: Monthly and yearly billing periods
- 🗄️ **MongoDB**: Scalable database with Prisma ORM
- 🎨 **Dark Mode**: Built-in light/dark theme support with next-themes
- 📱 **Responsive Design**: Tailwind CSS for modern, mobile-friendly UI
- ⚡ **Type-Safe**: Full TypeScript support across the stack
- 🔄 **Real-time Webhooks**: Stripe webhook integration for subscription events

## Tech Stack

- **Frontend**: React 18, Next.js 14, TypeScript
- **Styling**: Tailwind CSS, Radix UI components
- **Database**: MongoDB, Prisma ORM
- **Authentication**: Kinde Auth
- **Payments**: Stripe
- **State Management**: TanStack Query (React Query)
- **UI Components**: Radix UI, Lucide React icons

## Getting Started

### Prerequisites

- Node.js 16+ and npm
- MongoDB database (local or cloud)
- Stripe account
- Kinde authentication setup

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/devwithmohit/Stripe_payment_gateway.git
cd stripe-subscriptions
```

2. **Install dependencies**

```bash
npm install
```

3. **Set up environment variables**
   Create a `.env.local` file in the root directory:

```env
# Kinde Auth
NEXT_PUBLIC_KINDE_CLIENT_ID=your_kinde_client_id
KINDE_CLIENT_SECRET=your_kinde_client_secret
KINDE_DOMAIN=your_kinde_domain
NEXT_PUBLIC_KINDE_REDIRECT_URI=http://localhost:3000/auth/callback
NEXT_PUBLIC_KINDE_LOGOUT_REDIRECT_URI=http://localhost:3000

# Stripe
STRIPE_PUBLIC_KEY=your_stripe_public_key
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret

# Database
DATABASE_URL=mongodb+srv://username:password@cluster.mongodb.net/stripe-subscriptions
```

4. **Generate Prisma Client**

```bash
npx prisma generate
```

5. **Run the development server**

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
src/
├── app/
│   ├── api/
│   │   ├── auth/          # Kinde authentication routes
│   │   └── webhooks/      # Stripe webhook handler
│   ├── auth/
│   │   └── callback/      # Auth callback page
│   ├── premium/           # Premium features page
│   ├── layout.tsx         # Root layout
│   ├── page.tsx           # Home page
│   └── globals.css        # Global styles
├── components/
│   ├── Hero.tsx           # Landing hero section
│   ├── Navbar.tsx         # Navigation bar
│   ├── Pricing.tsx        # Pricing display
│   ├── PaymentLink.tsx    # Payment integration
│   ├── ModeToggle.tsx     # Dark mode toggle
│   ├── providers/         # Context providers
│   └── ui/                # Reusable UI components
├── db/
│   └── prisma.ts          # Prisma client instance
└── lib/
    ├── stripe.ts          # Stripe utilities
    └── utils.ts           # Helper functions

prisma/
└── schema.prisma          # Database schema
```

## Available Scripts

```bash
# Development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run linting
npm run lint

# Generate Prisma Client
npx prisma generate
```

## Database Schema

### User Model

- Stores user information with Kinde authentication
- Tracks subscription plan (free/premium)
- Maintains Stripe customer ID

### Subscription Model

- Links users to their active subscriptions
- Supports monthly and yearly billing periods
- Tracks subscription dates

## Stripe Integration

The application handles:

- Customer creation
- Subscription creation and management
- Payment processing
- Webhook events for subscription updates
- Subscription cancellation

## Authentication Flow

1. User clicks "Sign In" → Kinde OAuth redirect
2. User authorizes and is redirected to callback
3. User data is stored in MongoDB
4. Session is established
5. User can access premium features upon subscription

## Webhook Handling

Stripe webhooks are processed at `/api/webhooks/stripe` to handle:

- `customer.subscription.updated`
- `customer.subscription.deleted`
- `payment_intent.succeeded`

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For issues and questions, please open an issue on the [GitHub repository](https://github.com/devwithmohit/Stripe_payment_gateway).

## Author

**Mohit** - [GitHub](https://github.com/devwithmohit)

---

**Happy coding! 🚀**
