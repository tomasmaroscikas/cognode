<template>
  <main class="landing-page">
    <section class="hero is-fullheight-with-navbar hero-gradient">
      <div class="hero-body">
        <div class="container">
          <p class="subtitle is-uppercase has-text-weight-semibold tag-text">
            Cognode
          </p>
          <h1 class="title is-1 has-text-white">
            AI services tailored for fast-moving teams
          </h1>
          <p class="lead has-text-white-bis">
            Build, ship, and maintain practical AI solutions without the overhead of a
            full platform. We focus on the essentials so you can stay focused on your
            customers.
          </p>
          <div class="buttons">
            <a class="button is-primary is-medium" href="#services">Explore services</a>
            <a class="button is-light is-medium" href="#contact">Talk to us</a>
          </div>
        </div>
      </div>
    </section>

    <section id="services" class="section section-spaced">
      <div class="container">
        <p class="overline">Services</p>
        <h2 class="title is-2">What we deliver</h2>
        <p class="section-lead">
          From quick prototypes to production-ready systems, we keep each engagement
          lightweight and focused on measurable outcomes.
        </p>
        <div class="columns is-multiline">
          <div class="column is-one-third" v-for="service in services" :key="service.title">
            <div class="box service-card">
              <h3 class="title is-4">{{ service.title }}</h3>
              <p class="service-copy">{{ service.copy }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="about" class="section section-spaced has-background-light">
      <div class="container">
        <p class="overline">About us</p>
        <h2 class="title is-2">Pragmatic partners for AI adoption</h2>
        <div class="columns is-vcentered">
          <div class="column is-two-thirds">
            <p class="section-lead">
              Cognode is a compact team of engineers and product strategists. We have
              shipped AI-powered features for SaaS companies, professional service
              firms, and startups that need to move quickly without sacrificing
              reliability.
            </p>
            <p class="section-lead">
              We collaborate closely with your stakeholders, translate goals into
              clear deliverables, and document every step so your team can maintain the
              solution long after launch.
            </p>
          </div>
          <div class="column">
            <div class="about-card box">
              <h3 class="title is-5">How we work</h3>
              <ul>
                <li>Discovery focused on the problem, not the hype.</li>
                <li>Prototype quickly with user feedback loops baked in.</li>
                <li>Production rollouts with monitoring and handover support.</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="contact" class="section section-spaced">
      <div class="container">
        <p class="overline">Contacts</p>
        <h2 class="title is-2">Let’s start with a short call</h2>
        <p class="section-lead">
          Tell us about your use case and we will suggest the fastest path to a
          working solution.
        </p>
        <div class="contact-panel box">
          <div>
            <h3 class="title is-4">Reach out</h3>
            <p>Email: <a href="mailto:info@cognode.lt">info@cognode.lt</a></p>
            <p>Phone: <a href="tel:+37061511111">+370 615 11111</a></p>
          </div>
          <div class="contact-actions">
            <a class="button is-primary is-medium" href="mailto:info@cognode.lt">
              Book a chat
            </a>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'LandingPage',
  data() {
    return {
      services: [
        {
          title: 'Applied AI consulting',
          copy: 'Clarify opportunities, assess feasibility, and design a roadmap aligned with your business goals.'
        },
        {
          title: 'Model development',
          copy: 'Custom models built on reliable data pipelines with strong evaluation practices.'
        },
        {
          title: 'Integration & automation',
          copy: 'Embed AI features into your existing tools and workflows without disrupting your team.'
        }
      ]
    }
  },
  created() {
    this.$store.commit('set', {
      title: 'Cognode',
      subtitle: 'AI services tailored for fast-moving teams',
      featureImage: this.$siteConfig.featureImage
    })
  }
}
</script>

<style scoped>
.landing-page {
  scroll-behavior: smooth;
}

.hero-gradient {
  background: linear-gradient(135deg, #0f1b47 0%, #1b3c6f 50%, #283b63 100%);
  padding-top: 3.25rem;
}

.tag-text {
  letter-spacing: 0.08em;
}

.lead {
  font-size: 1.25rem;
  max-width: 720px;
  margin-top: 1rem;
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.section-spaced {
  padding-top: 6rem;
  padding-bottom: 6rem;
  scroll-margin-top: 4.5rem;
}

.overline {
  text-transform: uppercase;
  letter-spacing: 0.1em;
  font-size: 0.85rem;
  color: #6b7280;
  margin-bottom: 0.5rem;
  font-weight: 700;
}

.section-lead {
  font-size: 1.1rem;
  color: #4b5563;
  max-width: 820px;
  line-height: 1.7;
}

.service-card {
  height: 100%;
  box-shadow: 0 12px 30px rgba(17, 24, 39, 0.08);
  border: none;
}

.service-copy {
  color: #4b5563;
  line-height: 1.6;
}

.about-card ul {
  padding-left: 1.25rem;
}

.about-card li {
  margin-bottom: 0.5rem;
  color: #374151;
}

.contact-panel {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1.5rem;
  padding: 2rem;
  box-shadow: 0 12px 30px rgba(17, 24, 39, 0.08);
  border: none;
}

.contact-panel p {
  margin-bottom: 0.25rem;
  color: #374151;
}

.contact-actions {
  flex-shrink: 0;
}

@media (max-width: 1023px) {
  .section-spaced {
    padding-top: 4rem;
    padding-bottom: 4rem;
  }

  .contact-panel {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
