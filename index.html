// Mark <html> so CSS knows JS-driven initial states should apply.
document.documentElement.classList.add('js');

document.getElementById('year').textContent = new Date().getFullYear();

// Helper: split text into per-character spans.
function splitChars(el) {
  const text = el.dataset.text || el.textContent;
  el.textContent = '';
  return [...text].map(ch => {
    const span = document.createElement('span');
    span.className = 'char';
    span.textContent = ch === ' ' ? ' ' : ch;
    el.appendChild(span);
    return span;
  });
}

// Helper: split text into per-word spans (preserves spaces).
function splitWords(el) {
  const text = el.textContent;
  el.textContent = '';
  return text.split(/(\s+)/).map(part => {
    if (/^\s+$/.test(part)) {
      el.appendChild(document.createTextNode(part));
      return null;
    }
    const span = document.createElement('span');
    span.className = 'word';
    span.textContent = part;
    el.appendChild(span);
    return span;
  }).filter(Boolean);
}

document.addEventListener('DOMContentLoaded', () => {

  // ---------- 1. Hero entrance (timeline) ----------
  const heroTitle = document.querySelector('.hero-title');
  splitChars(heroTitle);

  const heroTimeline = anime.timeline({
    easing: 'easeOutExpo',
  });

  heroTimeline
    .add({
      targets: '.hero-title .char',
      opacity: [0, 1],
      translateY: [80, 0],
      rotateZ: [18, 0],
      scale: [0.6, 1],
      duration: 1100,
      delay: anime.stagger(55, { start: 200 }),
      easing: 'easeOutElastic(1, .7)',
    })
    .add({
      targets: '.hero-sub',
      opacity: [0, 1],
      translateY: [20, 0],
      duration: 700,
    }, '-=600')
    .add({
      targets: '.hero-underline path',
      strokeDashoffset: [600, 0],
      duration: 1400,
      easing: 'easeInOutQuad',
    }, '-=500')
    .add({
      targets: '.scroll-cue',
      opacity: [0, 0.8],
      translateY: [-10, 0],
      duration: 600,
    }, '-=600');

  // Subtle continuous shimmer on the gradient title.
  anime({
    targets: '.hero-title',
    backgroundPositionX: ['0%', '200%'],
    duration: 6000,
    easing: 'linear',
    loop: true,
  });

  // Bouncing scroll cue dot.
  anime({
    targets: '.scroll-cue span',
    translateY: [0, 10],
    opacity: [{ value: 1 }, { value: 0.2 }],
    duration: 1200,
    easing: 'easeInOutSine',
    direction: 'alternate',
    loop: true,
  });

  // ---------- 2. Floating background orbs ----------
  anime({
    targets: '.orb-1',
    translateX: () => anime.random(-80, 120),
    translateY: () => anime.random(-60, 100),
    scale: [1, 1.15],
    duration: 12000,
    easing: 'easeInOutSine',
    direction: 'alternate',
    loop: true,
  });
  anime({
    targets: '.orb-2',
    translateX: () => anime.random(-120, 60),
    translateY: () => anime.random(-80, 80),
    scale: [1, 1.1],
    duration: 14000,
    easing: 'easeInOutSine',
    direction: 'alternate',
    loop: true,
  });
  anime({
    targets: '.orb-3',
    translateX: () => anime.random(-100, 100),
    translateY: () => anime.random(-100, 60),
    scale: [1, 1.2],
    duration: 16000,
    easing: 'easeInOutSine',
    direction: 'alternate',
    loop: true,
  });

  // ---------- 3. Scroll-triggered reveals ----------
  const aboutText = document.querySelector('.about-text');
  if (aboutText) splitWords(aboutText);

  const animateSection = (section) => {
    if (section.dataset.animated) return;
    section.dataset.animated = 'true';

    // Animate the section title; the gold underline grows via CSS once `.is-revealed` is added.
    const title = section.querySelector('.section-title');
    if (title) {
      anime({
        targets: title,
        opacity: [0, 1],
        translateY: [30, 0],
        duration: 800,
        easing: 'easeOutExpo',
        complete: () => title.classList.add('is-revealed'),
      });
    }

    // About: stagger words.
    if (section.classList.contains('about')) {
      anime({
        targets: section.querySelectorAll('.about-text .word'),
        opacity: [0, 1],
        translateY: [20, 0],
        duration: 700,
        delay: anime.stagger(35, { start: 200 }),
        easing: 'easeOutQuad',
      });
    }

    // Projects: grid stagger reveal.
    const cards = section.querySelectorAll('.card');
    if (cards.length) {
      anime({
        targets: cards,
        opacity: [0, 1],
        translateY: [40, 0],
        scale: [0.95, 1],
        duration: 800,
        delay: anime.stagger(80, { start: 250, grid: [3, 3], from: 'first' }),
        easing: 'easeOutCubic',
      });
    }
  };

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        animateSection(entry.target);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });

  document.querySelectorAll('.reveal').forEach(s => observer.observe(s));

  // ---------- 4. Card hover: parallax glow + tilt ----------
  document.querySelectorAll('.card').forEach(card => {
    let raf = null;
    card.addEventListener('mousemove', (e) => {
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      const px = (x / rect.width) * 100;
      const py = (y / rect.height) * 100;

      // Update CSS variables for the radial-gradient ::before.
      card.style.setProperty('--mx', px + '%');
      card.style.setProperty('--my', py + '%');

      // Subtle 3D tilt.
      const rx = ((y / rect.height) - 0.5) * -6;
      const ry = ((x / rect.width) - 0.5) * 6;
      if (raf) cancelAnimationFrame(raf);
      raf = requestAnimationFrame(() => {
        card.style.transform = `perspective(800px) rotateX(${rx}deg) rotateY(${ry}deg) translateY(-4px)`;
      });
    });
    card.addEventListener('mouseleave', () => {
      anime.remove(card);
      anime({
        targets: card,
        rotateX: 0,
        rotateY: 0,
        translateY: 0,
        scale: 1,
        duration: 600,
        easing: 'spring(1, 80, 12, 0)',
      });
    });
  });

  // ---------- 5. Cursor glow follow ----------
  const glow = document.querySelector('.cursor-glow');
  if (glow && window.matchMedia('(hover: hover)').matches) {
    let mouseX = 0, mouseY = 0;
    let curX = 0, curY = 0;

    document.addEventListener('mousemove', (e) => {
      mouseX = e.clientX;
      mouseY = e.clientY;
      glow.style.opacity = '1';
    });
    document.addEventListener('mouseleave', () => { glow.style.opacity = '0'; });

    const tick = () => {
      curX += (mouseX - curX) * 0.12;
      curY += (mouseY - curY) * 0.12;
      glow.style.left = curX + 'px';
      glow.style.top = curY + 'px';
      requestAnimationFrame(tick);
    };
    tick();
  }

});
