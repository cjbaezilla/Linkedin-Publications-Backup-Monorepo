# Building Your Own Web AI Assistant: A Complete Hands-On Guide with CodeIgniter4, Next.js, and OpenRouter

## Executive Summary

This comprehensive guide walks you through building a fully functional AI-powered chat assistant from scratch. The project combines the robust backend capabilities of CodeIgniter 4, a modern PHP framework that has powered web applications for nearly two decades, with the cutting-edge frontend features of Next.js 16, all connected to OpenRouter's powerful AI API infrastructure.

What makes this project special is its simplicity paired with enterprise-grade architecture. You get a clean, modern chat interface where users can interact with AI models, while the backend handles secure communication with OpenRouter's extensive model catalog. The system is designed to be easily deployable, maintainable, and extensible. Every decision in this architecture was made with learning and customization in mind, so you'll never feel locked into someone else's way of doing things.

By the end of this guide, you'll have a complete working AI chat application that you can run locally, customize to your needs, and deploy to production. Whether you're a beginner looking to learn modern web development or an experienced developer wanting to understand how these technologies integrate, this hands-on project delivers real value. You'll walk away with working code, a solid understanding of how the pieces fit together, and plenty of ideas for extending the system in directions that interest you most.

Ready to see it in action? Head over to the live working example at [GitHub Repository](https://github.com/cjbaezilla/Building-Your-First-Web-AI-Assistant-Hands-On-Tutorial) and explore the code as you work through the guide. It's a great way to get oriented before diving in.

## Project Overview

This AI chat assistant represents a modern approach to building intelligent web applications. The architecture follows industry best practices by separating concerns between frontend and backend while maintaining clean communication channels. This separation isn't just about following patterns. It's about creating a system where you can swap out components without breaking everything else.

### What This Project Does

At its core, the application allows users to send text prompts to an AI model and receive intelligent responses. The frontend provides a user-friendly chat interface where messages appear in a conversation-style layout that feels natural and intuitive. When a user types a message and hits send, the frontend forwards it to the backend API, which then communicates with OpenRouter's AI services. The response flows back through the same path and displays elegantly formatted text to the user.

The system handles the complete conversation lifecycle with grace and reliability. It receives user input and validates that something meaningful was provided. It securely transmits the request to OpenRouter's API, protecting your API keys from ever reaching the browser. It processes the AI's response, handling various response formats that different models might return. Finally, it presents everything beautifully in the chat interface, where Markdown rendering ensures that AI responses with code blocks, lists, and formatting display correctly.

What you're building here isn't just a toy. It's the foundation for something much bigger. Think of it as your launchpad for exploring AI-powered features in future projects.

### Technology Stack

The backend uses [CodeIgniter 4](https://codeigniter.com/user_guide/index.html), a PHP framework known for its small footprint and exceptional performance. CodeIgniter 4 provides a modern PHP development experience with strong typing support, proper namespace usage, and a powerful routing system that makes creating RESTful APIs straightforward. The framework handles HTTP requests elegantly, manages your API endpoints, and securely communicates with external services without requiring you to write low-level curl commands or handle socket connections manually.

CodeIgniter has a passionate community that's been building with it since 2006. That means excellent documentation, answers to almost any question you might have, and a framework that's been battle-tested in production environments ranging from small startups to enterprise-scale applications. When you choose CodeIgniter, you're joining a community of developers who've refined their skills with this tool.

The frontend leverages [Next.js 16](https://nextjs.org/docs/app/getting-started), the latest version of Vercel's React framework featuring the App Router architecture. Next.js provides server-side rendering capabilities that make your pages load faster and are better for SEO. It offers automatic code splitting so users only download the JavaScript they need. The optimized development experience includes hot reloading, clear error messages, and a smooth workflow that makes building React applications genuinely enjoyable.

The UI uses [Tailwind CSS](https://tailwindcss.com/docs) for styling, a utility-first approach that lets you build custom designs without ever leaving your HTML. It also uses React Markdown for rendering formatted responses, which means your AI conversations can include code examples, bold text, lists, and more without any extra effort from you.

OpenRouter serves as the AI gateway, providing access to hundreds of AI models from various providers through a unified API. This project uses the nvidia/nemotron-3-nano-30b-a3b:free model, which offers impressive capabilities at absolutely no cost to you. The free tier gives you plenty of room to learn, experiment, and build your understanding before you ever need to spend money. When you're ready to explore other models, you can easily switch to any of the hundreds available in the [OpenRouter catalog](https://openrouter.ai/models). You'll find everything from lightning-fast models optimized for speed to powerful models designed for complex reasoning.

### Technology Stack Overview

| Component | Technology | Purpose |
|-----------|------------|---------|
| Backend Framework | CodeIgniter 4 | RESTful API development |
| Frontend Framework | Next.js 16 | React-based UI with App Router |
| Styling | Tailwind CSS | Utility-first CSS framework |
| AI Provider | OpenRouter | Unified gateway to multiple AI models |
| Default Model | nvidia/nemotron-3-nano-30b-a3b:free | Free model with solid capabilities |
| HTTP Client | Guzzle | PHP HTTP client for API calls |

Each technology in this stack has been carefully chosen to work together seamlessly. You get a backend that's lightweight yet powerful, a frontend that's modern and responsive, and an AI integration that gives you flexibility for the future.

## Architecture Deep Dive

Understanding the architecture helps you appreciate why the system works the way it does and makes future modifications intuitive. You'll find that once you understand the flow, extending the system becomes surprisingly straightforward.

### How The Pieces Connect

The application follows a client-server architecture with two main components living in separate directories. The `server` directory contains the CodeIgniter 4 backend application, while the `client` directory holds the Next.js frontend. These two components communicate over HTTP through RESTful API endpoints, standard web technology that works reliably across any network.

When a user interacts with the chat interface, several things happen behind the scenes, each step building on the last. First, the browser sends a POST request to the Next.js API route at `/api/chat`. This API route acts as a proxy, forwarding the request to the CodeIgniter backend at `http://localhost:8080/api/chat`. The backend then validates the request, attaches the OpenRouter API key (securely, on the server side where users can't see it), and sends the prompt to OpenRouter's AI service. Once the response arrives, it flows back through the same chain in reverse.

This proxy architecture provides several real benefits that matter in practice. The API key never touches the client browser since all OpenRouter communication happens server-side. That's security you can count on. You can implement rate limiting at the proxy layer to prevent abuse, add request logging to debug issues, or implement authentication to control who can use your AI. Additionally, the frontend remains completely decoupled from the specific AI provider, which means you could switch from OpenRouter to another service later without touching a single line of frontend code. You could even add a caching layer in front of your backend to store previous responses and reduce API calls.

### Data Flow Example

Let's trace a complete conversation flow to understand exactly how data moves through the system. This detailed walkthrough will help you visualize what's happening at every step.

A user types "Hello, how are you?" in the chat input and clicks Send. The React component captures this input immediately and calls the `sendChatMessage` function from the API library. This function sends a POST request to `/api/chat` with a JSON body containing `{ "prompt": "Hello, how are you?" }`.

Next.js receives this request at `app/api/chat/route.ts` and extracts the body. It then makes its own HTTP request to the backend, forwarding the exact same JSON to `http://localhost:8080/api/chat`. This is where the real work happens. Your backend is doing all the heavy lifting so your frontend stays light and fast.

The CodeIgniter controller receives the request, checks for the OpenRouter API key in environment variables (failing gracefully if it's missing), constructs the proper OpenRouter API payload following their expected format, and uses Guzzle HTTP client to send the request to OpenRouter's servers. The AI processes the prompt and returns a response, which the controller captures and returns as JSON to Next.js. This whole exchange typically happens in just a few seconds, depending on the model and your network speed.

When Next.js receives the response from CodeIgniter, it passes it back to the original caller without modification. The React component receives this response, extracts the text content, and updates the message state to display the AI's reply beautifully. The entire cycle completes seamlessly, and your user sees their conversation flowing naturally.

## Server-Side: CodeIgniter 4

The backend application lives in the `server` directory and provides the API that powers the AI chat functionality. CodeIgniter 4 brings modern PHP practices to a framework that has served developers admirably for nearly two decades. If you've worked with older PHP code, you'll appreciate how clean and organized CodeIgniter 4 feels. It embraces modern patterns while staying true to what made the framework great.

### Directory Structure

The CodeIgniter 4 project structure follows a clear organization pattern that makes finding things intuitive. The `app` directory contains your application code, while `system` holds the framework's core files. Your work primarily happens in the `app` folder, where you'll spend most of your time building features.

### Directory Structure Overview

| Directory | Location | Description |
|-----------|----------|-------------|
| app/Config | server/app/Config | Application configuration files |
| app/Controllers | server/app/Controllers | API endpoint handlers |
| app/Filters | server/app/Filters | Request/response processing |
| public | server/public | Web root, entry point for requests |
| system | server/system | Framework core files |
| app | client/app | Next.js App Router pages and routes |
| lib | client/lib | Utility functions and API helpers |
| public | client/public | Static assets |

The `app/Config` directory contains all configuration files, the control center for your application. Here you find `Database.php` for database connections, `Routes.php` for defining API endpoints, `Filters.php` for request filtering including CORS, and numerous other configuration files that control how the application behaves. When you need to change something about how your app works, this is usually where you'll start looking.

The `app/Controllers` directory is where your API endpoints live. Each controller class handles a specific set of related functionality, keeping your code organized and maintainable. The `OpenRouter.php` controller manages all AI chat interactions, while `Home.php` handles the default landing page. Controllers are where incoming requests meet your application logic.

The `app/Filters` directory contains filter classes that can process requests before they reach controllers or responses before they return to clients. The custom `Cors.php` filter handles cross-origin requests from the frontend elegantly, ensuring your frontend and backend can talk to each other without browser security getting in the way.

The `public` directory is the web root, what visitors access when they navigate to your server. It contains `index.php`, the entry point for all requests, and your `.htaccess` file for URL rewriting. When you deploy to production, this is the folder that gets exposed to the web.

### Key Configuration Files

The `.env` file holds critical configuration values that your application needs to function. This includes database credentials, application settings, and most importantly, your OpenRouter API key. Think of it as your application's configuration headquarters. Never share this file or commit it to version control, as it contains secrets that would let someone else use your API quota.

The database configuration in `app/Config/Database.php` defines how the application connects to databases. The default configuration uses MySQL, which works great, but you can switch to PostgreSQL, SQLite, or other databases by modifying this file. CodeIgniter's database abstraction means you can change databases without rewriting your queries.

Routing configuration in `app/Config/Routes.php` defines which controller methods respond to which URLs. Here's the current setup:

```php
<?php

use CodeIgniter\Router\RouteCollection;

$routes->get('/', 'Home::index');
$routes->post('/api/chat', 'OpenRouter::chat');
$routes->options('/api/chat', 'OpenRouter::options');
```

The current configuration creates three routes: the home page at `/`, the chat API at `/api/chat`, and an OPTIONS endpoint for CORS preflight requests at `/api/chat` with any HTTP method. Clean, simple, and exactly what you need.

Filter configuration in `app/Config/Filters.php` manages which filters apply to requests:

```php
class Filters extends BaseFilters
{
    public array $aliases = [
        'cors'          => Cors::class,
        'csrf'          => CSRF::class,
        // ... other aliases
    ];

    public array $globals = [
        'before' => [
            'cors',
        ],
        'after' => [
        ],
    ];
}
```

The CORS filter is registered globally, meaning it runs on every request before the controller code executes. This ensures that cross-origin requests from your Next.js frontend always receive proper CORS headers. It's like having a friendly receptionist who always makes sure visitors have what they need before they meet the team.

### The OpenRouter Controller

The `OpenRouter.php` controller is the heart of the backend, handling all communication with the AI service. Let's examine each part of this controller to understand how it works. This is where the magic happens.

```php
<?php

namespace App\Controllers;

use GuzzleHttp\Client;

class OpenRouter extends BaseController
{
    public function options(): \CodeIgniter\HTTP\Response
    {
        return $this->response
            ->setHeader('Access-Control-Allow-Origin', '*')
            ->setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS')
            ->setHeader('Access-Control-Allow-Headers', 'Content-Type')
            ->setStatusCode(200);
    }

    public function chat(): \CodeIgniter\HTTP\Response
    {
        $this->response->setHeader('Access-Control-Allow-Origin', '*');
        $this->response->setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS');
        $this->response->setHeader('Access-Control-Allow-Headers', 'Content-Type');

        if ($this->request->getMethod() === 'options') {
            return $this->response->setStatusCode(200);
        }

        $apiKey = getenv('OPENROUTER_API_KEY');
        
        if (empty($apiKey)) {
            return $this->response->setJSON(['error' => 'API key not configured'])->setStatusCode(500);
        }

        $prompt = $this->request->getVar('prompt') ?? 'Hello';

        $payload = [
            'model' => 'nvidia/nemotron-3-nano-30b-a3b:free',
            'input' => [
                ['role' => 'user', 'content' => $prompt]
            ]
        ];

        $client = new Client();

        try {
            $response = $client->post('https://openrouter.ai/api/v1/responses', [
                'headers' => [
                    'Authorization' => 'Bearer ' . $apiKey,
                    'Content-Type' => 'application/json',
                    'HTTP-Referer' => "https://baeza.ai",
                    'X-Title' => 'Baeza AI',
                ],
                'json' => $payload,
                'timeout' => 120,
                'verify' => false,
            ]);

            $body = json_decode($response->getBody()->getContents(), true);

            return $this->response->setJSON($body);
        } catch (\Exception $e) {
            return $this->response->setJSON(['error' => $e->getMessage())->setStatusCode(500);
        }
    }
}
```

The controller begins by defining an `options()` method that handles CORS preflight requests. When browsers make cross-origin requests with methods like POST or headers beyond simple ones, they first send an OPTIONS request to check if the server permits the actual request. This method returns the appropriate headers with a 200 status code, essentially saying "yes, I'm happy to talk to you." This happens automatically behind the scenes, and your users never notice it.

The main `chat()` method handles the actual AI conversation. It begins by setting CORS headers on the response, ensuring the frontend can receive the response properly. It then checks if this is a preflight OPTIONS request and handles it accordingly. This dual handling ensures everything works smoothly regardless of how the browser decides to make its request.

The controller retrieves the OpenRouter API key from environment variables using `getenv('OPENROUTER_API_KEY')`. If no API key is configured, it returns an error response with a 500 status code, preventing the request from failing silently or sending malformed requests to the API. It's better to fail clearly than to fail confusingly.

The user prompt comes from the request body via `$this->request->getVar('prompt')`. If no prompt is provided, it defaults to 'Hello', ensuring the API always has something to work with. This graceful fallback prevents errors when someone hits your endpoint unexpectedly.

The payload sent to OpenRouter specifies the model as `nvidia/nemotron-3-nano-30b-a3b:free`, which is a free model offering surprisingly good capabilities. The `input` array contains the conversation messages, with the user's prompt added as a user role message. OpenRouter's format is clean and straightforward to work with.

The controller uses Guzzle's HTTP client to make the API request. Guzzle is the gold standard for PHP HTTP requests. It handles all the complexity of making HTTP calls so you can focus on what matters. It POSTs to OpenRouter's responses endpoint at `https://openrouter.ai/api/v1/responses` (see the [OpenRouter API Reference](https://openrouter.ai/docs/api/reference/overview) for complete documentation on what's possible).

The request includes a 120-second timeout, giving the AI plenty of time to generate responses even for complex queries. The `verify => false` option disables SSL certificate verification, which is sometimes necessary in development environments with self-signed certificates. Just make sure you remove this in production to keep your connections secure.

The response from OpenRouter is parsed as JSON and returned directly to the frontend. If any exception occurs during the request, it's caught and returned as an error response with a 500 status code, giving the frontend enough information to display a helpful error message to the user.

### CORS Configuration

Cross-Origin Resource Sharing (CORS) is a security mechanism that restricts web pages from making requests to different domains. It's one of those things that sounds complicated but is actually straightforward once you understand it. Since your Next.js frontend runs on a different port (typically 3000) than your CodeIgniter backend (8080), you need CORS configuration to allow them to communicate. Without it, browsers would block the requests for security reasons.

The project implements CORS in two places for redundancy and reliability. First, a global filter in `app/Filters/Cors.php` runs on every request:

```php
<?php

namespace App\Filters;

use CodeIgniter\Filters\FilterInterface;
use CodeIgniter\HTTP\RequestInterface;
use CodeIgniter\HTTP\ResponseInterface;

class Cors implements FilterInterface
{
    public function before(RequestInterface $request, $arguments = null)
    {
        $response = service('response');
        
        $response->setHeader('Access-Control-Allow-Origin', '*');
        $response->setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS');
        $response->setHeader('Access-Control-Allow-Headers', 'Content-Type');
        
        if ($request->getMethod() === 'options') {
            return $response->setStatusCode(200);
        }
        
        return null;
    }

    public function after(RequestInterface $request, ResponseInterface $response, $arguments = null)
    {
        return $response;
    }
}
```

This filter sets the appropriate headers: `Access-Control-Allow-Origin: *` allows requests from any origin (useful for development), `Access-Control-Allow-Methods` specifies permitted HTTP methods, and `Access-Control-Allow-Headers` lists allowed request headers. Together, these headers tell browsers "yes, it's okay for code from other domains to talk to me."

Additionally, the OpenRouter controller explicitly sets these headers on every response. This double implementation ensures CORS works reliably regardless of which endpoint is accessed. Sometimes belts and suspenders is exactly the right approach.

In production, you might want to restrict the allowed origin to your specific frontend domain rather than using the wildcard `*`. You can do this by changing the header value from `'*'` to your actual domain like `'https://yourfrontend.com'`. This is more secure and is one of the first things you'll want to update when moving to production.

### API Endpoints

The backend exposes two main endpoints that the frontend uses. Understanding these endpoints helps you debug issues and plan extensions.

### API Endpoints Summary

| Endpoint | Method | Request Body | Response | Description |
|----------|--------|--------------|----------|-------------|
| /api/chat | POST | `{"prompt": "message"}` | AI response JSON | Main chat endpoint |
| /api/chat | OPTIONS | Empty | CORS headers | CORS preflight handler |

The primary endpoint is `POST /api/chat`, which accepts a JSON body with a `prompt` field containing the user's message. It returns the raw response from OpenRouter, which includes the AI's generated text along with metadata like model information and token usage. If an error occurs, it returns a JSON object with an `error` field describing what went wrong. This endpoint is the workhorse of your application.

The second endpoint is `OPTIONS /api/chat`, which handles CORS preflight requests. Browsers automatically send this before making POST requests from JavaScript to verify the server accepts cross-origin requests. It's a quick check-in that happens before the real conversation starts. It returns an empty response with appropriate CORS headers and a 200 status code.

## Client-Side: Next.js 16 with App Router

The frontend application in the `client` directory provides the user interface for interacting with the AI assistant. Built with Next.js 16 and the App Router, it demonstrates modern React development patterns with server components, API routes, and client-side interactivity. The result is a snappy, responsive application that users love interacting with.

### Understanding the App Router

Next.js 16 introduces the App Router as the default approach for building applications, replacing the older Pages Router. The App Router brings several improvements that make your applications faster and easier to build. It represents years of learning from the Next.js team about what makes React development productive.

In the App Router, every file in the `app` directory corresponds to a route in your application. The `page.tsx` file in the root `app` directory defines the home page at `/`, while `app/chat/page.tsx` defines the chat page at `/chat`. This file-based routing is intuitive and requires no complex configuration. You just create files and they work.

Components in the App Router can be either server components or client components. Server components run on the server and can directly access databases, APIs, and other server-side resources without sending extra requests. They render to HTML before reaching the browser, improving initial load performance dramatically. Client components use the `'use client'` directive and run in the browser, enabling interactivity like form submissions, state management, and browser APIs. The choice of which to use is one of the most powerful aspects of the App Router.

The `app/layout.tsx` file defines the root layout, which wraps all pages in your application:

```tsx
import type { Metadata } from "next";
import { Geist, Geist_Mono } from "next/font/google";
import "./globals.css";

const geistSans = Geist({
  variable: "--font-geist-sans",
  subsets: ["latin"],
});

const geistMono = Geist_Mono({
  variable: "--font-geist-mono",
  subsets: ["latin"],
});

export const metadata: Metadata = {
  title: "Create Next App",
  description: "Generated by create next app",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="en">
      <body
        className={`${geistSans.variable} ${geistMono.variable} antialiased`}
      >
        {children}
      </body>
    </html>
  );
}
```

In the App Router, `layout.tsx` files define shared UI that persists across page navigations. This root layout contains the HTML structure, fonts, and global styles that apply to every page in your application. When users navigate between pages, only the content changes. The layout stays stable, making transitions feel instant.

### Directory Structure

The client directory contains several important folders and files, each with a specific purpose.

The `app` directory is the heart of your Next.js application. Inside it, `page.tsx` serves as the landing page, currently showing a basic template that you can customize to match your vision. The `chat` subdirectory contains the main chat interface at `chat/page.tsx`, where users spend most of their time. The `api` subdirectory contains API route handlers, with `api/chat/route.ts` providing the proxy endpoint that forwards requests to the backend. Everything has its place.

The `lib` directory holds utility code that your components use. The `api.ts` file contains functions for communicating with your backend API, providing a clean interface that keeps your UI code simple and focused on presentation. When you need to change how your frontend talks to the backend, there's one place to look.

The `public` directory contains static assets like images, fonts, and SVG files that the browser can load directly without any processing. These are the unchanging pieces of your application.

The configuration files in the root include `package.json` defining dependencies and scripts, `next.config.ts` for Next.js configuration, `tsconfig.json` for TypeScript settings, and environment variable files. These files are your project's foundation.

### Key Frontend Files

### Key Frontend Files

| File | Path | Purpose |
|------|------|---------|
| Root Layout | app/layout.tsx | Wraps all pages, defines HTML structure |
| Home Page | app/page.tsx | Landing page entry point |
| Chat Page | app/chat/page.tsx | Main chat interface |
| API Route | app/api/chat/route.ts | Proxy to backend |
| API Library | lib/api.ts | TypeScript functions for API calls |
| Global Styles | app/globals.css | Tailwind and custom styles |

The `app/page.tsx` file serves as the landing page. Currently, it displays the default Next.js starter template with links to documentation and deployment options. You can customize this to create a welcoming landing page for your AI chat application, perhaps with a brief description of what the AI assistant can do and a button to navigate to the chat page. First impressions matter.

The `app/chat/page.tsx` file contains the actual chat interface, where the magic happens:

```tsx
'use client';

import { useState } from 'react';
import { sendChatMessage } from '@/lib/api';
import ReactMarkdown from 'react-markdown';
import remarkGfm from 'remark-gfm';

export default function ChatPage() {
  const [prompt, setPrompt] = useState('');
  const [messages, setMessages] = useState<Array<{ role: string; content: string }>>([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    
    if (!prompt.trim()) return;

    setLoading(true);
    setError(null);

    const userMessage = { role: 'user', content: prompt };
    setMessages((prev) => [...prev, userMessage]);

    try {
      const response = await sendChatMessage(prompt);

      if (response.error) {
        setError(response.error);
      } else {
        const outputText = response.output_text || '';
        const messageItem = response.output?.find((item: any) => item.type === 'message');
        const textContent = messageItem?.content?.find((c: any) => c.type === 'output_text');
        const content = outputText || textContent?.text || 'No response';
        const assistantMessage = { role: 'assistant', content };
        setMessages((prev) => [...prev, assistantMessage]);
      }
    } catch (err) {
      setError(err instanceof Error ? err.message : 'An error occurred');
    } finally {
      setLoading(false);
      setPrompt('');
    }
  };

  return (
    <div className="max-w-2xl mx-auto p-4">
      <h1 className="text-2xl font-bold mb-4">Chat with AI</h1>

      <div className="space-y-4 mb-4">
        {messages.map((message, index) => (
          <div
            key={index}
            className={`p-3 rounded-lg ${
              message.role === 'user' 
                ? 'bg-blue-100 ml-auto' 
                : 'bg-gray-100'
            }`}
          >
            <p className="font-semibold text-sm">{message.role}</p>
            <div className="prose prose-sm max-w-none">
              <ReactMarkdown remarkPlugins={[remarkGfm]}>
                {message.content}
              </ReactMarkdown>
            </div>
          </div>
        ))}
      </div>

      {error && (
        <div className="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded mb-4">
          {error}
        </div>
      )}

      <form onSubmit={handleSubmit} className="flex gap-2">
        <input
          type="text"
          value={prompt}
          onChange={(e) => setPrompt(e.target.value)}
          placeholder="Type your message..."
          className="flex-1 p-2 border rounded-lg"
          disabled={loading}
        />
        <button
          type="submit"
          disabled={loading || !prompt.trim()}
          className="px-4 py-2 bg-blue-500 text-white rounded-lg disabled:opacity-50"
        >
          {loading ? 'Thinking...' : 'Send'}
        </button>
      </form>
    </div>
  );
}
```

This client component manages conversation state, handles form submissions, and renders messages beautifully. It uses React's `useState` hook to track the message history, loading state, and any errors. When the user submits a message, it calls the `sendChatMessage` function from the API library, adds the user's message to the display immediately (so it feels responsive), waits for the response, and then adds the AI's reply.

The chat page uses React Markdown to render message content, which means the AI's responses can include formatted text, code blocks, lists, and other Markdown elements. This is particularly useful when the AI provides code examples or structured information. Seeing properly formatted code makes a huge difference in usability.

The `app/api/chat/route.ts` file implements a Next.js API route that acts as a proxy:

```typescript
import { NextRequest, NextResponse } from 'next/server';

const API_URL = process.env.NEXT_PUBLIC_API_URL || 'http://localhost:8080';

export async function POST(request: NextRequest) {
  try {
    const body = await request.json();

    const response = await fetch(`${API_URL}/api/chat`, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(body),
    });

    const data = await response.json();

    return NextResponse.json(data, { status: response.status });
  } catch (error) {
    return NextResponse.json(
      { error: 'Failed to connect to the server' },
      { status: 500 }
    );
  }
}
```

Instead of calling the backend directly from the browser, the frontend calls this local API route, which then forwards the request to the CodeIgniter backend. This proxy pattern keeps your backend URL hidden from users and enables future enhancements like caching, authentication, or rate limiting without changing any frontend code.

The `lib/api.ts` file provides a clean, typed interface for making API calls:

```typescript
export interface ChatRequest {
  prompt: string;
}

export interface ChatResponse {
  id?: string;
  model?: string;
  output_text?: string;
  output?: Array<{
    type?: string;
    role?: string;
    content?: Array<{
      type: string;
      text?: string;
    }>;
  }>;
  usage?: {
    input_tokens?: number;
    output_tokens?: number;
    total_tokens?: number;
  };
  error?: string;
}

const API_URL = process.env.NEXT_PUBLIC_API_URL || 'http://localhost:8080';

export async function sendChatMessage(prompt: string): Promise<ChatResponse> {
  try {
    const response = await fetch('/api/chat', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ prompt }),
    });

    const data = await response.json();

    if (!response.ok) {
      throw new Error(data.error || `HTTP error! status: ${response.status}`);
    }

    return data;
  } catch (error) {
    if (error instanceof TypeError && error.message === 'Failed to fetch') {
      throw new Error('Network error: Unable to connect to the server');
    }
    throw error;
  }
}
```

It exports a `sendChatMessage` function that takes a prompt string and returns a promise resolving to the API response. The file also exports TypeScript interfaces for the request and response shapes, ensuring type safety throughout the application. TypeScript will catch mistakes before they reach your users. That's a huge win for code quality.

### Styling with Tailwind CSS

The project uses Tailwind CSS for styling, a utility-first CSS framework that lets you build custom designs directly in your HTML. Instead of writing custom CSS files, you apply pre-built utility classes to elements. It might feel strange at first if you're used to traditional CSS, but once you try it, you'll appreciate how fast you can iterate on designs.

The `app/globals.css` file imports Tailwind and configures the theme. It sets up CSS variables for light and dark mode, defines color schemes, and imports the typography plugin for nice Markdown rendering. The configuration is minimal but powerful.

Tailwind's utility classes appear throughout the components. For example, `flex` makes an element a flex container, `p-4` adds padding, `rounded-lg` rounds corners, and `bg-blue-500` sets background colors. The `dark:` prefix lets you define different styles for dark mode, which is becoming increasingly expected by users.

Tailwind's responsive prefixes let you design for different screen sizes elegantly. Classes like `sm:items-start` apply different styles at the small breakpoint, while base classes apply to all sizes. Building responsive layouts becomes almost effortless.

## Environment Variables and Configuration

Environment variables are critical to the application's functionality, storing sensitive information and configuration that changes between environments. Getting these right from the start makes your development workflow much smoother.

### Environment Variables Reference

| Variable | Location | Required | Description |
|----------|----------|----------|-------------|
| OPENROUTER_API_KEY | server/.env | Yes | API key for OpenRouter AI services |
| database.default.* | server/.env | No | Database connection settings |
| CI_ENVIRONMENT | server/.env | Yes | Set to "development" or "production" |
| NEXT_PUBLIC_API_URL | client/.env.local | Yes | Backend API URL (e.g., http://localhost:8080) |

The CodeIgniter backend reads from the `.env` file in the `server` directory. This file should never be committed to version control, as it contains sensitive data that would cause problems if exposed.

```env
# Database Configuration
database.default.hostname = localhost
database.default.database = your_database_name
database.default.username = your_username
database.default.password = your_password
database.default.DBDriver = MySQLi
database.default.port = 3306

# Application Environment
CI_ENVIRONMENT = development

# OpenRouter API Key
OPENROUTER_API_KEY = your_openrouter_api_key_here
```

The key variable is `OPENROUTER_API_KEY`, which provides authentication with OpenRouter's services. You obtain this key by creating an account at openrouter.ai and generating a new API key from your dashboard. The process takes about two minutes and then you're ready to go.

### Frontend Environment Variables

The Next.js frontend uses `.env.local` for environment variables, which is the Next.js convention for environment-specific configuration.

```env
# Backend API URL
NEXT_PUBLIC_API_URL=http://localhost:8080
```

Unlike backend environment variables, frontend variables that start with `NEXT_PUBLIC_` are exposed to the browser build. The key frontend variable is `NEXT_PUBLIC_API_URL`, which tells the frontend where to find the backend API. For local development, this is set to `http://localhost:8080`, matching the port where the CodeIgniter development server runs.

### Security Considerations

Your `.env` files contain secrets that must be protected absolutely. Never commit them to git or other version control systems. The project includes `.env` in `.gitignore` for exactly this reason, but double-check that it's working before you push anywhere.

In production, you set environment variables through your hosting provider's dashboard rather than using .env files. Most hosting platforms provide a secure way to configure environment variables that won't be accidentally committed. Services like Vercel, Heroku, and AWS all handle this elegantly.

When deploying, ensure your OpenRouter API key remains private. If someone obtains your key, they could use your API quota at your expense. Rotate your keys periodically and use the key with the minimum required permissions. These small security habits pay off in the long run.

## Installation and Setup

Now let's get the project running on your local machine. I'll walk through setting up both the backend and frontend step by step, making sure nothing gets missed.

### Prerequisites

Before you begin, ensure you have the necessary tools installed on your computer. Having everything ready before you start makes the process much smoother.

### Prerequisites Checklist

| Requirement | Backend (CodeIgniter) | Frontend (Next.js) |
|-------------|----------------------|-------------------|
| Runtime | PHP 8.2+ | Node.js 18.17+ |
| Package Manager | Composer | npm (included with Node.js) |
| Database | MySQL (optional) | Not required |
| Extensions | mbstring, intl, pdo | None additional |

For the backend, you need PHP 8.2 or higher with the following extensions: mbstring for string handling, intl for internationalization, and pdo for database connectivity. You'll also need Composer, PHP's dependency manager, to install CodeIgniter and its packages. A local MySQL database or MySQL server installed (like XAMPP or WAMP for Windows) provides the database if you want to store chat history.

For the frontend, you need Node.js 18.17 or later and npm (which comes with Node.js). The installation is straightforward and works similarly on Windows, macOS, and Linux. If you've built any web projects before, you probably already have these installed.

### Installing the Backend (CodeIgniter 4)

The server directory already contains a CodeIgniter 4 installation, but let's verify everything is properly configured so you can proceed with confidence.

First, navigate to the server directory in your terminal:

```
cd ./server
```

Or if you're using a Unix-like terminal:

```
cd /path/to/ai_chatbot_publication/server
```

Install the PHP dependencies using Composer:

```
composer install
```

This command reads the `composer.json` file and installs all required packages, including CodeIgniter framework files and Guzzle for HTTP requests. Composer is incredibly efficient, and this should only take a minute or two.

Now you need to configure your environment. The project includes a `.env` file, but you should review and update the settings. Open the `.env` file in a text editor and verify the database settings match your local MySQL configuration. If you're just testing the AI chat functionality without storing data, the database configuration won't affect the core features. You can skip this step entirely for now.

Most importantly, you need a valid OpenRouter API key. Visit openrouter.ai, create an account (it takes seconds with Google or GitHub signup), navigate to the dashboard, and generate a new API key. Replace the example key in the `.env` file with your actual key:

```
OPENROUTER_API_KEY = your_actual_api_key_here
```

With these steps complete, your backend is ready to run. You've already accomplished the hardest part of backend setup.

### Installing the Frontend (Next.js)

Now let's set up the Next.js frontend. Navigate to the client directory:

```
cd ./client
```

Install the Node.js dependencies:

```
npm install
```

This reads `package.json` and installs all required packages: Next.js, React, React DOM, TypeScript types, Tailwind CSS, and other development dependencies. The process takes a few minutes as it downloads packages from the npm registry, but progress bars keep you informed the whole time.

After installation completes, your client directory is ready for development. You now have everything you need to build something amazing.

### Running the Application Locally

With both installations complete, you can now run the full application. You'll need two terminal windows, one for the backend and one for the frontend. It sounds like extra work, but it's the standard development workflow and you'll get used to it quickly.

**Starting the Backend**

In your first terminal, navigate to the server directory and start PHP's built-in development server:

```
cd ./server
php spark serve
```

PHP Spark is CodeIgniter's command-line tool that starts a development server with all the features you need. By default, it runs on port 8080. You should see output indicating the server is running, typically showing "CodeIgniter Development Server started on http://localhost:8080". Keep this terminal window open as long as you want to use the application.

**Starting the Frontend**

In your second terminal, navigate to the client directory and start the Next.js development server:

```
cd ./client
npm run dev
```

This starts the Next.js development server, typically on port 3000. You'll see output with "Ready" when compilation completes, and you can access the application at http://localhost:3000. The first build takes a moment, but subsequent startups are lightning-fast thanks to Next.js caching.

**Testing the Chat**

Open your browser and navigate to http://localhost:3000/chat to access the chat interface. You should see a clean chat interface with an input field and send button that looks polished and professional.

Type a message like "Hello, how are you?" and press Send or click the button. After a brief moment (depending on the AI model's response time), you should see your message appear in the chat followed by the AI's response. The response is rendered with Markdown formatting, so code blocks and other formatting display properly. Watching it work for the first time is genuinely exciting.

If you encounter errors, check both terminal windows for error messages. Common issues include the backend not running, an invalid API key, or network connectivity problems. Every problem has a solution, and the error messages will guide you toward it.

## Understanding How the Code Works Together

Let's take a deeper look at how the frontend and backend communicate, making troubleshooting easier and enabling customization. Understanding this flow gives you power over your application.

### The Frontend API Call Chain

When you send a message in the chat interface, here's exactly what happens in the code.

The user's message gets captured in the `prompt` state variable through the input's `onChange` handler. When the form submits, the `handleSubmit` function prevents the default browser behavior and initiates the API call without reloading the page.

The `sendChatMessage` function from `lib/api.ts` is called with the prompt. This function uses the native Fetch API to POST to `/api/chat` (the local Next.js API route). The request includes a JSON body with the prompt string.

The Next.js API route in `app/api/chat/route.ts` receives this request. It extracts the body, reads the backend URL from environment variables, and makes its own fetch call to `http://localhost:8080/api/chat`, forwarding the exact same JSON payload. The proxy works perfectly.

### The Backend Processing

On the backend, the CodeIgniter routing system directs the request to the `OpenRouter` controller's `chat` method based on the route definition in `Routes.php`. Routing is one of those things that just works when configured correctly.

The controller method first sets CORS headers on the response, which is essential for the browser to accept the response from a different origin. It then retrieves the API key from environment variables and constructs the OpenRouter API payload following their expected format.

The Guzzle HTTP client sends the request to OpenRouter with appropriate headers including authentication. The response comes back as JSON, which the controller passes through to the frontend with `$this->response->setJSON($body)`. It's elegantly simple.

### Response Handling Back to Frontend

The Next.js API route receives the response from CodeIgniter and uses `NextResponse.json()` to forward it to the original caller. This preserves the response status code, so errors from OpenRouter are properly propagated up the chain.

The `sendChatMessage` function receives this response, checks if it was successful (response.ok is true), parses the JSON, and returns it to the component. If there was an error, it throws an exception with a descriptive message that helps users understand what went wrong.

The chat component receives the response data, extracts the text content (handling both the `output_text` field and nested `output` array that OpenRouter's newer API format uses), and adds the assistant's message to the message history. The React component automatically re-renders to display the new message, and your user sees the complete conversation.

### Error Handling

The system handles errors at multiple levels, which makes debugging easier and user experience better.

### Error Handling Overview

| Error Type | Location | User Message | Troubleshooting |
|------------|----------|---------------|-----------------|
| Network error | Frontend API | "Network error: Unable to connect to the server" | Check backend is running on port 8080 |
| API key missing | Backend | "API key not configured" | Verify OPENROUTER_API_KEY in .env file |
| API error | Backend | Error message from OpenRouter | Check API key validity and model availability |
| Timeout | Backend | Exception message from Guzzle | Increase timeout value or try faster model |
| CORS error | Browser console | Cross-origin blocked | Verify CORS filter is configured |

In the frontend API library, network errors are caught and converted to user-friendly messages like "Network error: Unable to connect to the server" when the fetch fails entirely. Users don't need to see technical details. They just need to know what happened.

API errors (non-2xx status codes) result in the response's error field being extracted and thrown as an exception. The chat component catches these and displays them in an error banner, allowing the user to see what happened and try again.

The backend catches exceptions from Guzzle and returns them as JSON errors with a 500 status code. This includes connection failures, API errors, and timeouts. The response includes the exception message for debugging, though in production you might want to mask specific error details for security.

## Production Deployment

When you're ready to share your application with the world, you'll need to deploy it to a production environment. The approach differs depending on your hosting provider, but you have options that fit various budgets and technical requirements.

### Deploying the Backend

For the CodeIgniter backend, you need a PHP hosting environment that supports PHP 8.2 or higher. Most shared hosting providers, VPS services, or platform-as-a-service options work well. You have plenty of choices.

Upload your `server` directory to your hosting account. The public-facing files should be in the `public` directory or whatever directory your host designates as the web root. Most hosts use `public_html` or `htdocs`. Read your host's documentation if you're unsure.

Configure your environment variables in your hosting control panel or through a `.env` file in your deployment. Set `CI_ENVIRONMENT = production` for security, and ensure your `OPENROUTER_API_KEY` is properly configured. Production mode enables important security features.

If your host uses Apache, the provided `.htaccess` file should handle URL routing automatically. For Nginx, you'll need to configure similar rewrite rules to route all requests through `index.php`. Most hosting platforms provide sample configurations you can follow.

Ensure the `writable` directory has proper permissions so CodeIgniter can write logs and cache files. Typically, setting this to 755 or 775 works, though some hosts require specific configurations. When in doubt, check your hosting provider's documentation.

### Deploying the Frontend

The Next.js frontend can be deployed in multiple ways depending on your hosting environment. You can use Vercel for the easiest deployment, deploy as a Node.js application, or export as static files for traditional shared hosting.

### Deployment Options Comparison

| Method | Best For | Difficulty | Backend Required |
|--------|----------|------------|------------------|
| Vercel | Next.js apps, quick deployment | Easiest | Separate hosting |
| Static Export | Shared PHP hosting | Easy | PHP hosting |
| Node.js App | VPS or Node hosting | Medium | Node.js hosting |

#### Option 1: Vercel Deployment

Vercel (the creators of Next.js) provides the easiest deployment experience by far. Connect your GitHub repository to Vercel, and it automatically detects the Next.js application, runs the build, and deploys it. You'll need to configure the `NEXT_PUBLIC_API_URL` environment variable in the Vercel dashboard to point to your deployed backend URL. This is the path of least resistance.

#### Option 2: Static Build for Shared Hosting

Shared hosting environments typically don't support Node.js applications, but you can deploy Next.js as static HTML files. This approach works great for simple hosting accounts that only provide PHP support. Yes, you can still run modern Next.js apps!

First, configure Next.js for static export by modifying `next.config.ts`:

```typescript
import type { NextConfig } from "next";

const nextConfig: NextConfig = {
  output: 'export',
  trailingSlash: true,
  images: {
    unoptimized: true,
  },
};

export default nextConfig;
```

The `output: 'export'` setting generates static HTML files instead of a Node.js server. The `trailingSlash: true` option adds trailing slashes to URLs, which works better with many shared hosting configurations. The `unoptimized: true` for images is required because the static export doesn't include Next.js's image optimization server.

Now build the application:

```
npm run build
```

This creates a `out` directory containing static HTML, CSS, JavaScript, and image files. Upload the entire contents of this directory to your shared hosting's web root (typically `public_html` or `htdocs`). The frontend will be accessible at your domain, and it will work just like any other website.

#### Option 3: Node.js Application

If your hosting supports Node.js applications, you can run the production build directly:

```
npm run build
npm start
```

This starts the Next.js server on port 3000 by default. You'll need to set up process management to keep the server running, which some hosting platforms handle automatically. Services like PM2 make this straightforward.

### Updating the Frontend Configuration

After deploying, remember to update your frontend's environment variables to point to the production backend URL. If your backend is at `https://api.yourdomain.com`, set `NEXT_PUBLIC_API_URL=https://api.yourdomain.com`.

The frontend and backend must be able to communicate, so ensure CORS headers on the backend allow requests from your frontend's domain. In production, replace the `Access-Control-Allow-Origin: *` with your specific frontend domain for better security.

### Shared Hosting Considerations

Shared hosting environments often have limitations that affect deployment. Here are some common challenges and solutions that will save you time.

### Shared Hosting Checklist

| Consideration | Backend (PHP) | Frontend (Static) |
|---------------|---------------|-------------------|
| PHP Version | Verify PHP 8.2+ support | Not applicable |
| Dependencies | Upload vendor folder if Composer unavailable | Use static export |
| Memory Limits | Adjust memory_limit in .htaccess | Not applicable |
| URL Rewriting | Test .htaccess rules | Works with default config |
| File Placement | public_html/api/ | public_html/ |

**Backend (PHP/CodeIgniter)**

PHP version constraints mean you should verify your host supports PHP 8.2 before committing to CodeIgniter 4. Many hosts offer PHP version selection through their control panels, so this is usually easy to check.

File system restrictions on shared hosting can prevent Composer from installing dependencies in the usual way. If you can't run Composer on the server, run it locally and upload the complete `vendor` directory along with your code. This takes more disk space but works reliably.

Memory limits might cause issues with larger AI responses. Configure PHP settings like `memory_limit` and `max_execution_time` appropriately, either through `.htaccess` or your hosting control panel. The defaults are conservative; you can increase them based on your needs.

URL rewriting often works differently on shared hosting. Test your deployment thoroughly and adjust the `.htaccess` rules if necessary to ensure routing works correctly.

**Frontend (Static Next.js)**

When deploying the Next.js frontend as static files to shared hosting, place the contents of the `out` directory in your public web folder. If you're hosting both frontend and backend on the same domain, you can place the frontend files in the root and the CodeIgniter backend in a subfolder (like `/api/`).

For example, if your shared hosting structure looks like this:
```
public_html/
  ├── index.html          (Next.js entry point)
  ├── chat/
  │   └── index.html     (Chat page)
  └── api/               (CodeIgniter backend)
      └── index.php
```

You'll need to ensure the backend routes don't conflict with frontend routes. One approach is to prefix all API routes in CodeIgniter or use a separate subdomain for the API.

If you encounter issues with page refreshes showing 404 errors, make sure the `.htaccess` file properly handles client-side routing. Next.js static exports generate an `index.html` for each folder, which typically works with default Apache configurations.

## Customization and Extension

Now that you understand the base system, you can extend it in many directions to add features and improve functionality. The architecture supports your ambitions.

### Extension Options

| Feature | Complexity | Backend Changes | Frontend Changes |
|---------|------------|-----------------|------------------|
| Change AI Model | Easy | Modify model field in controller | None required |
| Conversation History | Medium | Accept messages array in request | Send full message history |
| User Authentication | Medium | Integrate CodeIgniter Shield | Add login/logout UI |
| Rate Limiting | Medium | Add Redis or database counters | None required |
| Streaming Responses | Advanced | Implement chunked transfer | Handle streaming chunks |
| Typing Indicator | Easy | None required | Add loading animation |
| Code Highlighting | Easy | None required | Add syntax highlighting library |
| Chat Export | Easy | None required | Add export to PDF/text |

### Changing the AI Model

The current implementation uses the nvidia/nemotron-3-nano-30b-a3b model, but OpenRouter offers hundreds of models with different capabilities, pricing, and performance characteristics. Finding the right model for your use case is part of the fun.

To use a different model, modify the `model` field in the OpenRouter controller's `$payload` array. For example, to use Anthropic's Claude:

```php
'model' => 'anthropic/claude-3-haiku',
```

Or for OpenAI's GPT models:

```php
'model' => 'openai/gpt-4-turbo',
```

Each model has different pricing and capabilities. Check OpenRouter's documentation for the full list and current pricing. Some models are free, while others require payment. You can also filter models by capability, speed, and cost through OpenRouter's model selection interface.

### Adding Conversation History

The current implementation treats each message independently, which is simple but limiting. To add conversation history, you need to modify how messages are stored and sent to the API. This is one of the most common enhancements people want.

In the frontend, the `messages` state already stores the conversation history. You can modify the API call to send this entire history instead of just the latest prompt:

```typescript
const response = await fetch('/api/chat', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ messages }),
});
```

On the backend, modify the controller to accept the messages array and pass it directly to OpenRouter instead of constructing a single user message. This enables the AI to maintain context across the conversation, making the experience feel much more natural.

### Implementing User Authentication

To add user accounts, you'll want to integrate CodeIgniter's authentication libraries. CodeIgniter Shield is the official authentication library that provides user login, registration, and session management out of the box with minimal configuration.

Install Shield through Composer, configure it in your application, and use its authentication helpers in your controllers. You'd then associate chat messages with user IDs, track usage per user, and provide personalized experiences that make your application stand out.

### Adding Rate Limiting

To prevent abuse and protect your API quota, implement rate limiting on your API endpoints. CodeIgniter doesn't include rate limiting by default, but you can implement it using Redis or database-backed counters, or through your web server configuration (like Nginx's rate limiting).

For a simple implementation, track the number of requests per IP address in a database table and block or throttle requests that exceed a threshold within a time window. This keeps your service available for legitimate users.

### Improving the UI

The current chat interface is functional but basic. You can enhance it in many ways that will delight your users.

Add streaming responses so users see the AI's response as it generates rather than waiting for the complete response. This creates a much more engaging experience. It requires modifying both the backend (to stream from OpenRouter) and frontend (to handle streaming chunks), but the result is worth the effort.

Implement typing indicators to show when the AI is processing. Add a visual "typing..." animation that displays while waiting for the response, giving users confidence that something is happening.

Enhance message rendering to support code syntax highlighting, image display, or interactive elements based on the AI's response type. Rich content makes conversations more useful.

Add conversation management features like saving chats, loading previous conversations, or exporting chats to PDF or text files. These features transform your chat app from a toy into a useful tool.

### Advanced OpenRouter Features

The OpenRouter Responses API unlocks powerful capabilities that can take your chat application to the next level. These features open up entirely new possibilities for what your AI assistant can do. The [Responses API documentation](https://openrouter.ai/docs/api-reference/responses/basic-usage) provides the foundation for understanding how these features work together.

**Reasoning Capabilities**

Some models support advanced reasoning that lets the AI show its thought process. You can configure how much effort the model puts into reasoning by adjusting the effort level in your request. The options range from minimal for quick answers to high for complex problems that benefit from step-by-step thinking. The [reasoning documentation](https://openrouter.ai/docs/api/reference/responses/reasoning) covers all the details you need to get started.

When reasoning is enabled, the response includes the model's internal reasoning alongside its final answer. This is particularly valuable for mathematical problems, logical analysis, or any situation where understanding how the AI reached its conclusion matters. You can see the reasoning unfold in real-time by enabling streaming, which makes the experience feel more interactive and transparent.

The reasoning feature works seamlessly with the existing API structure. Simply add the reasoning parameter to your payload with your desired effort level, and OpenRouter handles the rest. The response includes both the reasoning trace and the generated text, giving you flexibility in how you display the results to users.

Here's how you enable reasoning in your CodeIgniter controller:

```php
$payload = [
    'model' => 'openai/o4-mini',
    'input' => [
        ['role' => 'user', 'content' => $prompt]
    ],
    'reasoning' => [
        'effort' => 'high'
    ],
    'max_output_tokens' => 9000,
];

$response = $client->post('https://openrouter.ai/api/v1/responses', [
    'headers' => [
        'Authorization' => 'Bearer ' . $apiKey,
        'Content-Type' => 'application/json',
    ],
    'json' => $payload,
    'timeout' => 120,
]);
```

The effort level options are minimal, low, medium, and high. Higher effort means more computational work the model performs, which translates to better reasoning for complex questions but also uses more tokens.

**Tool Calling**

The Responses API supports tool calling, which lets the AI invoke functions you define. This means your chat assistant can perform real actions like fetching weather data, querying databases, or calling external APIs. The possibilities expand dramatically when your AI can actually do things rather than just talk about them. The [tool calling documentation](https://openrouter.ai/docs/api/reference/responses/tool-calling) shows you exactly how to set this up.

You define tools using the standard OpenAI function calling format, specifying the function name, description, and parameters. When the model determines that a tool would help answer the user's question, it returns a function call that you execute on your server. You then feed the result back to the model, which incorporates it into its response.

The system handles multiple tool calls in parallel when needed, and you have full control over which tools are available and when they're used. You can let the model decide automatically, disable tool calling entirely, or force specific tools to be called. This flexibility lets you build exactly the behavior you need.

Here's how you define tools and make requests in PHP:

```php
$weatherTool = [
    'type' => 'function',
    'name' => 'get_weather',
    'description' => 'Get the current weather in a location',
    'strict' => null,
    'parameters' => [
        'type' => 'object',
        'properties' => [
            'location' => [
                'type' => 'string',
                'description' => 'The city and state, e.g. San Francisco, CA',
            ],
            'unit' => [
                'type' => 'string',
                'enum' => ['celsius', 'fahrenheit'],
            ],
        ],
        'required' => ['location'],
    ],
];

$payload = [
    'model' => 'openai/o4-mini',
    'input' => [
        [
            'type' => 'message',
            'role' => 'user',
            'content' => [
                ['type' => 'input_text', 'text' => 'What is the weather in San Francisco?']
            ]
        ]
    ],
    'tools' => [$weatherTool],
    'tool_choice' => 'auto',
    'max_output_tokens' => 9000,
];
```

When the model calls a tool, the response includes a function_call object with the name and arguments. You execute the function, then pass the result back to continue the conversation. The tool_choice parameter lets you control whether the model can use tools at all, let it decide automatically, or force a specific tool to be called.

**Web Search**

Your AI assistant can access real-time information from the internet through OpenRouter's web search integration. This solves one of the biggest limitations of language models: their knowledge cutoff date. With web search, your chatbot can answer questions about current events, latest technology, or any topic requiring up-to-date information. The [web search documentation](https://openrouter.ai/docs/api/reference/responses/web-search) explains everything you need to know about enabling this feature.

The search plugin returns results with proper citations, allowing you to show users where information came from. This transparency builds trust and lets users verify answers themselves. You can control how many search results the model uses, balancing thoroughness against response speed.

It's worth noting that web search incurs additional costs beyond standard API calls. The extra computation for searching and processing web results means you'll want to consider when this feature provides genuine value versus when your model's existing knowledge is sufficient. For applications where current information matters, like news assistants or research tools, the additional cost delivers real value.

Here's how to enable web search in your requests:

```php
$payload = [
    'model' => 'openai/o4-mini',
    'input' => [
        ['role' => 'user', 'content' => 'What is the latest version of React?']
    ],
    'plugins' => [
        ['id' => 'web', 'max_results' => 3]
    ],
    'max_output_tokens' => 9000,
];

$response = $client->post('https://openrouter.ai/api/v1/responses', [
    'headers' => [
        'Authorization' => 'Bearer ' . $apiKey,
        'Content-Type' => 'application/json',
    ],
    'json' => $payload,
    'timeout' => 120,
]);
```

The response includes annotation objects with url_citation types, giving you the exact source URLs and the text positions they reference. Some models also support an online variant that has web search built in, so you can append ":online" to the model name instead of using the plugins parameter.

### Responses API Parameters

The Responses API accepts a range of parameters that let you customize how the AI generates responses. Here's a comprehensive overview of the most commonly used options:

| Parameter | Type | Description |
|-----------|------|-------------|
| `model` | string | The AI model to use for generating responses |
| `input` | array | Array of message objects containing conversation history |
| `reasoning` | object | Configuration for reasoning effort level (effort: minimal/low/medium/high) |
| `tools` | array | Array of tool definitions for function calling |
| `tool_choice` | string/object | Controls which tools the model can use |
| `plugins` | array | Plugins like web search (e.g., [{ id: 'web', max_results: 3 }]) |
| `max_output_tokens` | integer | Maximum number of tokens in the response |
| `temperature` | float | Controls randomness in output (0.0 to 2.0) |
| `stream` | boolean | Enable streaming responses for real-time output |
| `metadata` | object | Optional metadata to track usage and organization |

The [full parameters documentation](https://openrouter.ai/docs/api-reference/responses/create-responses) covers every available option with examples for each use case.

## Troubleshooting Common Issues

Even well-configured applications sometimes encounter problems. Here are solutions to common issues you might encounter. You'll be able to work through these quickly.

### Troubleshooting Quick Reference

| Problem | Error Message | Solution |
|---------|---------------|----------|
| Connection refused | "Connection refused" | Verify backend runs on port 8080 |
| API key missing | "API key not configured" | Check OPENROUTER_API_KEY in .env |
| CORS errors | Console shows CORS error | Verify Cors filter and headers |
| Slow responses | Long wait times | Try faster model or check network |
| SSL errors | Certificate verification failed | Update CA certificates |
| Deployment 404 | Page not found on refresh | Check .htaccess for routing |

### Connection Refused Errors

If you see "Connection refused" errors when sending messages, the backend server likely isn't running. Verify the CodeIgniter server is started with `php spark serve` and running on port 8080. Check that your firewall isn't blocking the connection. These checks solve most connection issues.

### API Key Errors

"API key not configured" errors mean the backend can't find your OpenRouter API key. Verify the key is set in the `.env` file with the correct variable name `OPENROUTER_API_KEY`. If you've recently modified the `.env` file, restart the backend server to pick up changes. Servers don't automatically reload environment files.

### CORS Errors

If your browser's console shows CORS errors, the backend isn't returning proper cross-origin headers. Verify the Cors filter is registered in `Filters.php` and the controller sets headers on responses. Check that both frontend and backend are running on different ports or domains as expected.

### Slow Response Times

AI API calls can take time, especially with complex prompts or busy models. If responses are slower than expected, try a faster model in the OpenRouter settings, check your network connection to OpenRouter's servers, or implement response caching for repeated queries. There are several angles to approach this from.

### SSL Certificate Errors

If you see SSL certificate verification errors, you might have `verify => false` in production, which is insecure. Instead, ensure your PHP environment has up-to-date CA certificates. On Linux, you can update CA certificates with your system's package manager. On Windows, PHP typically uses the system's certificate store. Keeping certificates updated is a good security practice anyway.

### Deployment Issues

When deploying to production, common issues include environment variables not being set, incorrect file permissions preventing writes to the writable directory, and routing not working because the web server isn't configured for CodeIgniter's URL structure. Address each by verifying hosting provider documentation and checking server error logs. Error logs are your friend. They tell you exactly what's wrong.

## Additional Resources

Here are official documentation and references to help you deepen your understanding and continue building. These resources will accelerate your learning.

**OpenRouter**

- [OpenRouter API Reference](https://openrouter.ai/docs/api/reference/overview) - Complete reference for the AI API endpoints, request/response formats, and authentication
- [OpenRouter Responses API Parameters](https://openrouter.ai/docs/api-reference/responses/create-responses) - Detailed documentation on all available parameters for customizing API requests
- [OpenRouter Models](https://openrouter.ai/models) - Browse available AI models, compare pricing, and find the right model for your needs

**CodeIgniter 4**

- [CodeIgniter 4 User Guide](https://codeigniter.com/user_guide/index.html) - Official documentation covering controllers, routing, database operations, configuration, and best practices

**Next.js**

- [Next.js App Router Documentation](https://nextjs.org/docs/app/getting-started) - Learn about the App Router architecture, server components, API routes, and deployment

**Tailwind CSS**

- [Tailwind CSS Documentation](https://tailwindcss.com/docs) - Complete reference for utility classes, configuration, and styling

**Working Example**

- [GitHub Repository](https://github.com/cjbaezilla/Building-Your-First-Web-AI-Assistant-Hands-On-Tutorial) - A working example that demonstrates the concepts covered in this guide

## Conclusion

You now have a complete, working AI chat assistant built with modern, industry-standard technologies. The project demonstrates clean architecture with separation between frontend and backend, proper security practices with API key protection, and extensibility for future enhancements. Everything is in place for you to build on this foundation.

This foundation opens many possibilities. You can enhance the AI's capabilities by connecting to different models, add rich features like conversation history and user accounts, or customize the interface to match your brand. The technologies you've learned, CodeIgniter 4 for robust PHP backends and Next.js 16 with App Router for modern React frontends, transfer directly to countless other projects you'll work on throughout your career.

As you continue developing, remember that the open source community provides extensive documentation and examples for both frameworks. The OpenRouter platform offers easy access to cutting-edge AI models with simple API integration. Your journey building AI-powered applications has never had a better starting point.

To see a working example of these concepts in action, check out the [GitHub repository](https://github.com/cjbaezilla/Building-Your-First-Web-AI-Assistant-Hands-On-Tutorial) that accompanies this guide. Seeing working code brings everything together.

Get out there and build something amazing!
