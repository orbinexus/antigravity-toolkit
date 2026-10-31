---
name: gsap-scrolltrigger-wizard
description: Orchestrates buttery-smooth scroll-driven cinematic animations, 3D card tilt physics, timeline choreographies, and Lenis smooth scrolling.
---

# GSAP & ScrollTrigger Cinematic Choreography

This skill guides the construction of award-winning, scroll-driven visual narratives and timeline orchestrations using GSAP (GreenSock) and ScrollTrigger.

## 1. Timeline Choreography & Scroll Binding

1. **ScrollTrigger Pinning & Scrubbing**:
   - Bind timeline progress to scroll position:
     ```javascript
     gsap.timeline({
       scrollTrigger: {
         trigger: "#hero-section",
         start: "top top",
         end: "+=1500",
         scrub: 1, // 1-second smooth spring catchup
         pin: true
       }
     })
     .from(".hero-card", { scale: 0.8, rotateX: 25, opacity: 0, stagger: 0.1 })
     .to(".hero-title", { y: -100, opacity: 0 }, "<");
     ```
2. **Lenis Inertial Smooth Scrolling**:
   - Synchronize GSAP `ScrollTrigger.update` with `lenis.on('scroll', ...)` for momentum-based, zero-jank page gliding.

## 2. 3D Tilt Physics & Interactive Stagger
- Use mousemove events to subtly transform 3D perspective cards (`rotateX`, `rotateY`) with transform-style `preserve-3d`.
- Respect user reduced motion preferences (`prefers-reduced-motion: reduce`) by disabling scrubbing on demand.
