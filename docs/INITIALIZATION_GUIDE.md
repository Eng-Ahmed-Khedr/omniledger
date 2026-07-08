# OmniLedger: Tech Stack Initialization Guide

## Overview
This document outlines the step-by-step initialization process for the OmniLedger financial analytics dashboard. Executing these steps in sequence resolves dependencies early and establishes a clean, enterprise-grade development environment.

## Phase 1: The Core Environment
- **Next.js** App Router and TypeScript provide the strict architectural skeleton required for processing high-velocity financial data.
Command: npx create-next-app@latest omniledger
## Phase 2: The UI Engine (shadcn/ui)
- **shadcn/ui** provides accessible, enterprise-grade components. It integrates seamlessly with **Tailwind CSS** to handle the visual layer.
Command: npx shadcn@latest init
Recommended Prompts during setup:
- Style: Default / New York
- Base color: Slate or Zinc
- CSS variables: Yes
## Phase 3: The State Manager (Redux Toolkit)
- **Redux Toolkit (RTK)** is essential for managing the continuous incoming stream of mock transaction data without triggering unnecessary UI re-renders.
Command: npm install @reduxjs/toolkit react-redux
## Phase 4: The Data Visualizer (Recharts)
- **Recharts** is a highly composable, lightweight charting library built natively for React, perfect for rendering dynamic data arrays.
Command: npm install recharts
## Phase 5: Iconography (Lucide React)
- **Lucide** provides clean, professional icons for the dashboard navigation and metric cards.
Command: npm install lucide-react
## Phase 6: Boilerplate Cleanup
- To ensure a blank canvas, navigate to **src/app/page.tsx** and **src/app/globals.css** and delete the default Next.js starter code.
