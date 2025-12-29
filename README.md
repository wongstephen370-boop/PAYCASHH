# PayCash - Caribbean Payment Platform

Accept payments easily with PayCash. A modern payment platform for entrepreneurs and businesses across Jamaica and the Caribbean.

## Project Structure

```
paycash/
├── app/                    # Next.js frontend (Next.js App Router)
│   ├── page.tsx           # Landing page
│   ├── login/             # Login page
│   ├── register/          # Registration page
│   ├── merchant-demo/     # Merchant demo dashboard
│   ├── admin-demo/        # Admin demo dashboard
│   └── dashboard/         # Protected merchant dashboard
├── backend/               # Express.js backend API
│   ├── app.js            # Main server file
│   ├── models/           # MongoDB schemas
│   ├── routes/           # API endpoints
│   ├── middleware/       # Auth and other middleware
│   └── config/           # Configuration files
├── components/            # React UI components
├── lib/                   # Utility functions
├── public/                # Static files
└── .do/                   # DigitalOcean configuration
```

## Quick Start

### Prerequisites
- Node.js 16+
- MongoDB Atlas account
- DigitalOcean account (optional, for deployment)
- Vercel account (optional, for frontend deployment)

### Local Development

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/paycash.git
cd paycash
```

2. **Setup Backend**
```bash
cd backend
npm install
cp .env.example .env.local
# Edit .env.local with your MongoDB URI and JWT secret
npm run dev
```

3. **Setup Frontend** (in a new terminal)
```bash
npm install
# Create .env.local in root
echo "NEXT_PUBLIC_API_URL=http://localhost:5000" > .env.local
npm run dev
```

4. **Access the app**
- Frontend: http://localhost:3000
- Backend: http://localhost:5000
- Register: http://localhost:3000/register
- Login: http://localhost:3000/login
- Demo: http://localhost:3000/merchant-demo

## Deployment

### Deploy Backend to DigitalOcean

See [DIGITALOCEAN_DEPLOYMENT.md](./DIGITALOCEAN_DEPLOYMENT.md) for complete instructions.

Quick steps:
1. Update `.do/app.yaml` with your GitHub repo and frontend URL
2. Push to GitHub with `.do/app.yaml` included
3. Go to DigitalOcean App Platform → Create App → Select GitHub repo
4. Copy the deployed URL and add to frontend environment variables

### Deploy Frontend to Vercel

1. Go to https://vercel.com
2. Import your GitHub repository
3. Add environment variable:
   - `NEXT_PUBLIC_API_URL` = your DigitalOcean backend URL
4. Deploy

## Features

- User registration and authentication with JWT
- Merchant dashboard with transaction history
- Payment links and QR code generation
- Admin dashboard for platform management
- Real-time transaction tracking
- Secure payment processing
- CORS-enabled API

## API Endpoints

### Authentication
- `POST /api/auth/register` - Create new account
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user

### Payments
- `POST /api/payments/create` - Create payment
- `GET /api/payments/history` - Get payment history
- `POST /api/payments/qr` - Generate QR code

### Merchants
- `GET /api/merchants/dashboard` - Get dashboard data
- `GET /api/merchants/transactions` - Get transactions
- `POST /api/merchants/payment-links` - Create payment link

### Admin
- `GET /api/admin/overview` - Platform overview
- `GET /api/admin/merchants` - List merchants
- `GET /api/admin/transactions` - All transactions
- `GET /api/admin/fees` - Revenue and fees

## Environment Variables

### Backend (.env)
```
MONGODB_URI=mongodb+srv://...
JWT_SECRET=your_secret_key
FRONTEND_URL=http://localhost:3000
NODE_ENV=development
PORT=5000
```

### Frontend (.env.local)
```
NEXT_PUBLIC_API_URL=http://localhost:5000
```

## Technologies

- **Frontend**: Next.js 16, React, TailwindCSS, TypeScript
- **Backend**: Node.js, Express, MongoDB
- **Database**: MongoDB Atlas
- **Hosting**: DigitalOcean (backend), Vercel (frontend)
- **Authentication**: JWT tokens
- **UI Components**: shadcn/ui

## Security

- Password hashing with bcrypt
- JWT token-based authentication
- CORS protection
- Rate limiting on API endpoints
- Environment variable protection
- Secure HTTP headers with Helmet

## Contributing

1. Create a feature branch: `git checkout -b feature/amazing-feature`
2. Commit changes: `git commit -m 'Add amazing feature'`
3. Push to branch: `git push origin feature/amazing-feature`
4. Open a Pull Request

## License

MIT License - feel free to use this project

## Support

For issues or questions, please open a GitHub issue or contact support.

## Roadmap

- Mobile app (React Native)
- Stripe payment integration
- Multi-currency support
- Advanced analytics
- Team management
- API keys for developers

