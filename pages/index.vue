<template>
  <main class="landing-page">
    <section class="hero is-fullheight-with-navbar hero-gradient">
      <div class="hero-body">
        <div class="container">
          <p class="subtitle is-uppercase has-text-weight-semibold tag-text">
            Cognode
          </p>
          <h1 class="title is-1 has-text-white">
            AI sprendimai sparčiai dirbančioms komandoms
          </h1>
          <p class="lead has-text-white-bis">
            Kuriame, diegiame ir prižiūrime praktiškus AI sprendimus be didelių platformos išlaidų. Susitelkiame į tai, kas svarbiausia, kad jūs galėtumėte susitelkti į savo klientus.
          </p>
          <div class="buttons">
            <a class="button is-primary is-medium" href="#services">Mūsų paslaugos</a>
            <a class="button is-light is-medium" href="#contact">Aptarkime</a>
          </div>
        </div>
      </div>
    </section>

    <section id="services" class="section section-spaced">
      <div class="container">
        <p class="overline">Paslaugos</p>
        <h2 class="title is-2">Sprendimai, kuriuos teikiame</h2>
        <p class="section-lead">
          Nuo greitų prototipų iki gamybai parengtų sistemų — kiekvieną užduotį atliekame paprastai ir susitelkiame į išmatuojamus rezultatus.
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
        <p class="overline">Apie mus</p>
        <h2 class="title is-2">Praktiškas AI diegimo partneris</h2>
        <div class="columns is-vcentered">
          <div class="column is-two-thirds">
            <p class="section-lead">
              „Cognode“ – kompaktiška inžinierių ir produktų strategų komanda. Kuriame dirbtinio intelekto funkcijas SaaS įmonėms, profesionalių paslaugų verslams ir startuoliams, kuriems reikia veikti greitai, neprarandant patikimumo.
            </p>
            <p class="section-lead">
              Dirbame kartu su jūsų suinteresuotosiomis šalimis, išgryniname tikslus į konkrečius, išmatuojamus rezultatus ir nuosekliai dokumentuojame procesą. Taip jūsų komanda gali sprendimą išlaikyti ir sėkmingai naudoti ilgą laiką po įdiegimo.
            </p>
          </div>
          <div class="column">
            <div class="about-card box">
              <h3 class="title is-5">Kaip mes dirbame</h3>
              <ul>
                <li>Susitelkiame į tikslą</li>
                <li>Greitai kuriame prototipus</li>
                <li>Nuolatinis naudotojų grįžtamasis ryšys</li>
                <li>Diegimas, stebėsena, palaikymas</li>
                <li>Mokymai</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="contact" class="section section-spaced">
      <div class="container">
        <p class="overline">Kontaktai</p>
        <h2 class="title is-2">Pradėkime nuo trumpo pokalbio</h2>
        <p class="section-lead">
          Papasakokite apie savo naudojimo atvejį, o mes pasiūlysime greičiausią kelią iki veikiančio sprendimo.
        </p>
        <div class="contact-panel box">
          <div>
            <h3 class="title is-4">Kontaktai</h3>
            <p>El. paštas: <a href="mailto:info@cognode.lt">info@cognode.lt</a></p>
            <p>Telefonas: <a href="tel:+37061511111">+370 686 78094</a></p>
          </div>
          <div class="contact-actions">
            <a class="button is-primary is-medium" href="mailto:info@cognode.lt">
              Rezervuokite pokalbį
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
          title: 'DI taikymo konsultacijos',
          copy: 'Padedame aiškiai įvardyti galimybes, įvertiname jų realumą ir parengiame veiksmų planą, atitinkantį jūsų verslo tikslus.'
        },
        {
          title: 'DI modelių kūrimas',
          copy: 'Individualiūs modeliai, paremti patikimais duomenų srautais ir tvirta vertinimo metodika.'
        },
        {
          title: 'Integravimas ir automatizavimas',
          copy: 'Integruojame DI funkcijas į jūsų naudojamus įrankius ir procesus — be trikdžių jūsų komandai.'
        },
        {
          title: 'DI mokymai',
          copy: 'Rengiame praktinius DI mokymus, kad jūsų komanda galėtų taikyti DI kasdieniuose darbuose ir kurti apčiuopiamą vertę.'
        }
      ]
    }
  },
  created() {
    this.$store.commit('set', {
      title: 'Cognode',
      subtitle: 'DI sprendimai sparčiai dirbančioms komandoms',
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
