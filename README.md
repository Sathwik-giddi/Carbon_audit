# Carbon Audit AI

> Automated carbon emissions auditing from industrial invoices, powered by AI.

[![Next.js](https://img.shields.io/badge/Next.js-15-black?logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3-38bdf8?logo=tailwind-css)](https://tailwindcss.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

Carbon Audit AI is a modern web application that transforms messy OCR-extracted invoice text into actionable carbon footprint reports. By leveraging AI-powered entity extraction, it automates what traditionally takes days of manual auditing into seconds.

### Key Features

- **AI-Powered Extraction** — Uses Genkit with Google AI to automatically extract electricity (kWh) and diesel (liters) values from unstructured invoice text
- **Real-Time Emission Calculations** — Computes CO2e emissions using IPCC & GHG Protocol standard emission factors
- **ISO 14064 Compliance Checks** — Automatically flags usage that exceeds industry benchmarks
- **Actionable Insights** — Provides tailored recommendations to reduce emissions
- **Audit History** — Tracks past audits locally for trend analysis
- **Responsive UI** — Built with shadcn/ui components and Tailwind CSS for a polished, accessible experience

## Why This Matters

Companies face increasing regulatory pressure to report greenhouse gas (GHG) emissions transparently. Manual carbon audits are:

- **Time-consuming** — Hours spent reading through invoices and spreadsheets
- **Error-prone** — Manual data entry introduces inconsistencies
- **Hard to scale** — Becomes unmanageable across multiple facilities

Carbon Audit AI reduces audit time from **days to seconds** by using AI to extract, calculate, and analyze emission data automatically.

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | Next.js 15 (App Router) |
| Language | TypeScript |
| Styling | Tailwind CSS + shadcn/ui |
| AI/ML | Genkit + Google AI (Gemini) |
| State | React Hooks + localStorage |
| Icons | Lucide React |
| Charts | Recharts |
| Forms | React Hook Form + Zod |

## Getting Started

### Prerequisites

- Node.js 20+
- npm or yarn

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/Sathwik-giddi/Carbon_audit.git
   cd Carbon_audit
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Set up environment variables**

   Create a `.env.local` file in the root directory:

   ```env
   GOOGLE_API_KEY=your_google_api_key_here
   ```

   > Get your API key from [Google AI Studio](https://aistudio.google.com/apikey)

4. **Run the development server**

   ```bash
   npm run dev
   ```

   Open [http://localhost:9002](http://localhost:9002) in your browser.

## How It Works

### 1. Input Invoice Text

Paste OCR-extracted text from utility bills, fuel receipts, or energy invoices:

```
Invoice #874
Electricity usage: 15,000 kWh
Diesel fuel: 800 liters
Billing period: March 2025
```

### 2. AI Extraction

The Genkit flow processes the text using a structured prompt to extract:
- Electricity consumption (kWh)
- Diesel consumption (liters)

### 3. Emission Calculation

Emissions are computed using standard emission factors:

| Source | Unit | Emission Factor |
|--------|------|-----------------|
| Electricity | 1 kWh | 0.233 kg CO2e |
| Diesel | 1 liter | 2.68 kg CO2e |

**Example:**
- Electricity: 15,000 x 0.233 = **3,495 kg CO2e**
- Diesel: 800 x 2.68 = **2,144 kg CO2e**
- **Total: 5,639 kg CO2e**

### 4. Compliance Check

Usage is compared against ISO 14064 benchmarks:
- Electricity > 12,000 kWh -> Warning flagged
- Diesel > 1,000 liters -> Warning flagged

### 5. Report & Recommendations

Users receive a comprehensive report with:
- Total emissions breakdown
- Compliance warnings
- Reduction strategies
- Educational FAQ section

## Project Structure

```
Carbon_audit/
├── src/
│   ├── ai/
│   │   ├── flows/
│   │   │   └── extract-invoice-data.ts   # AI extraction flow
│   │   ├── dev.ts                         # Genkit dev entry
│   │   └── genkit.ts                      # Genkit configuration
│   ├── app/
│   │   ├── page.tsx                       # Home / input page
│   │   ├── result/
│   │   │   └── page.tsx                   # Results dashboard
│   │   ├── history/
│   │   │   └── page.tsx                   # Audit history
│   │   ├── layout.tsx                     # Root layout
│   │   ├── actions.ts                     # Server actions
│   │   └── globals.css                    # Global styles
│   ├── components/
│   │   ├── ui/                            # shadcn/ui components
│   │   ├── main-nav.tsx                   # Navigation
│   │   └── site-header.tsx                # Site header
│   ├── hooks/                             # Custom React hooks
│   └── lib/
│       └── utils.ts                       # Utility functions
├── docs/
│   └── blueprint.md                       # Project blueprint
├── public/
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── next.config.ts
```

## Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Run TypeScript type checking |
| `npm run genkit:dev` | Start Genkit development UI |

## Emission Factors

All emission factors are based on **IPCC** and **GHG Protocol** guidelines:

- **Grid Electricity**: 0.233 kg CO2e per kWh (global average grid factor)
- **Diesel Fuel**: 2.68 kg CO2e per liter (Scope 1 direct emissions)

Compliance thresholds are derived from **ISO 14064** benchmarks for medium-sized industrial operations.

## Future Roadmap

- [ ] PDF/CSV report export for compliance documentation
- [ ] Firebase Firestore integration for cloud-synced audit history
- [ ] Multi-facility dashboard with comparative analytics
- [ ] Additional emission sources (natural gas, refrigerants, fleet)
- [ ] ERP system integration (SAP, Oracle)
- [ ] Advanced AI models (fine-tuned extraction for diverse invoice formats)
- [ ] Real-time emission factor updates by region
- [ ] Carbon offset recommendations and marketplace integration

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

## Authors

- **Sathwik R.**
- **Sowmya Mucharla**

Built during Summer 2025 Internship | Focused on climate tech, NLP, and carbon automation.
