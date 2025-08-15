# Bluedottech
Bizpage
/*
Blue Dot Technology - Next.js + Tailwind CSS Starter
SEO-friendly layout with dynamic meta tags and complete page set
*/

// package.json
{
  "name": "blue-dot-technology",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  },
  "dependencies": {
    "next": "14.0.0",
    "react": "18.2.0",
    "react-dom": "18.2.0"
  },
  "devDependencies": {
    "autoprefixer": "^10.4.0",
    "postcss": "^8.4.0",
    "tailwindcss": "^3.3.0"
  }
}

// tailwind.config.js
module.exports = {
  content: ["./pages/**/*.{js,ts,jsx,tsx}", "./components/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors: {
        navy: "#131B62",
        blue: "#3754ED",
        yellow: "#DBF059",
        lightgray: "#E4E2DC"
      }
    }
  },
  plugins: []
};

// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {}
  }
};

// components/Layout.js
import Head from 'next/head';
import Link from 'next/link';

export default function Layout({ title, description, children }) {
  const siteTitle = title ? `${title} | Blue Dot Technology` : 'Blue Dot Technology';
  const siteDescription = description || 'Smart systems. Simple solutions. Modern bookkeeping, automation, and AI services to help your business grow.';

  return (
    <>
      <Head>
        <title>{siteTitle}</title>
        <meta name="description" content={siteDescription} />
        <meta property="og:title" content={siteTitle} />
        <meta property="og:description" content={siteDescription} />
        <meta property="og:type" content="website" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
      </Head>
      <header className="bg-navy text-white p-4 flex justify-between">
        <h1 className="font-bold"><Link href="/">Blue Dot Technology</Link></h1>
        <nav className="space-x-4">
          <Link href="/services">Services</Link>
          <Link href="/about">About</Link>
          <Link href="/contact">Contact</Link>
        </nav>
      </header>
      <main className="font-sans bg-lightgray min-h-screen">
        {children}
      </main>
      <footer className="bg-navy text-white p-4 text-center">
        © {new Date().getFullYear()} Blue Dot Technology. All rights reserved.
      </footer>
    </>
  );
}

// pages/index.js
import Layout from '../components/Layout';

export default function Home() {
  return (
    <Layout title="Home" description="Blue Dot Technology - bookkeeping, automation, and AI services for small businesses.">
      <section className="bg-navy text-white py-20 text-center">
        <h1 className="text-4xl font-bold">Smart systems. Simple solutions.</h1>
        <p className="mt-4 text-lg">Helping small businesses scale with modern bookkeeping, automation, and AI.</p>
        <a href="/contact" className="mt-6 inline-block bg-yellow text-navy px-6 py-3 rounded-lg font-semibold hover:bg-blue hover:text-white transition">Get Started</a>
      </section>
      <section className="py-16 px-6 max-w-6xl mx-auto grid md:grid-cols-4 gap-8">
        {[
          { title: 'Bookkeeping', desc: 'Modern, accurate bookkeeping and accounts payable solutions.' },
          { title: 'Workflow Automation', desc: 'Streamline repetitive tasks to save time and reduce errors.' },
          { title: 'AI Agents & GPTs', desc: 'Custom AI tools to support and enhance your business operations.' },
          { title: 'Business Process Optimization', desc: 'Analyze and improve systems for efficiency and scalability.' }
        ].map((service, idx) => (
          <div key={idx} className="bg-white p-6 rounded-lg shadow hover:shadow-lg transition">
            <h3 className="text-xl font-bold text-navy mb-2">{service.title}</h3>
            <p className="text-gray-700">{service.desc}</p>
          </div>
        ))}
      </section>
    </Layout>
  );
}

// pages/services.js
import Layout from '../components/Layout';

export default function Services() {
  return (
    <Layout title="Services" description="Explore Blue Dot Technology services for bookkeeping, automation, AI, and business optimization.">
      <div className="max-w-4xl mx-auto py-12 px-6">
        <h2 className="text-3xl font-bold text-navy mb-6">Our Services</h2>
        <ul className="space-y-6">
          <li>
            <h3 className="text-xl font-semibold">Bookkeeping & Accounts Payable</h3>
            <p>Accurate, timely, and automated financial tracking to keep your business running smoothly.</p>
          </li>
          <li>
            <h3 className="text-xl font-semibold">Workflow Automation</h3>
            <p>Eliminate repetitive tasks and optimize processes with tailored automation solutions.</p>
          </li>
          <li>
            <h3 className="text-xl font-semibold">AI Agents & Custom GPTs</h3>
            <p>Integrate AI tools that understand your business and deliver consistent results.</p>
          </li>
          <li>
            <h3 className="text-xl font-semibold">Business Process Optimization</h3>
            <p>Analyze and improve systems to help your company grow efficiently and sustainably.</p>
          </li>
        </ul>
      </div>
    </Layout>
  );
}

// pages/about.js
import Layout from '../components/Layout';

export default function About() {
  return (
    <Layout title="About" description="Learn about Blue Dot Technology and our mission to help small businesses scale.">
      <div className="max-w-4xl mx-auto py-12 px-6">
        <h2 className="text-3xl font-bold text-navy mb-6">About Us</h2>
        <p>Blue Dot Technology was founded to bring modern, efficient solutions to small and medium-sized businesses. With expertise in bookkeeping, automation, and AI, we help clients save time, improve accuracy, and create scalable systems.</p>
      </div>
    </Layout>
  );
}

// pages/contact.js
import Layout from '../components/Layout';

export default function Contact() {
  return (
    <Layout title="Contact" description="Get in touch with Blue Dot Technology for a consultation or more information.">
      <div className="max-w-4xl mx-auto py-12 px-6">
        <h2 className="text-3xl font-bold text-navy mb-6">Contact Us</h2>
        <form action="https://formspree.io/f/yourformid" method="POST" className="bg-white p-6 rounded-lg shadow space-y-4">
          <input type="text" name="name" placeholder="Your Name" className="w-full p-3 border border-gray-300 rounded" required />
          <input type="email" name="email" placeholder="Your Email" className="w-full p-3 border border-gray-300 rounded" required />
          <textarea name="message" placeholder="Your Message" rows="5" className="w-full p-3 border border-gray-300 rounded" required></textarea>
          <button type="submit" className="bg-blue text-white px-6 py-3 rounded hover:bg-navy transition">Send Message</button>
        </form>
      </div>
    </Layout>
  );
}

// styles/globals.css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  font-family: system-ui, sans-serif;
}
