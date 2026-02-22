<template>
    <section class="hero">
        <div class="hero-wrapper">

            <!-- LEFT SIDE -->
            <div class="hero-text">
                <h1>Hi, I’m Rahul.</h1>
                <p class="subtitle">
                    I build scalable cloud-native applications.
                </p>
                <p class="tech">
                    .NET • AWS • Vue • Angular
                </p>
            </div>

            <!-- RIGHT SIDE -->
            <div class="image-wrapper" @mousemove="handleMove" @mouseleave="resetTilt">
                <img src="@/assets/profile.jpeg" alt="Rahul" ref="imageRef" />
            </div>

        </div>
    </section>
</template>
  
<script setup>
import { ref } from "vue"
import { gsap } from "gsap"

const imageRef = ref(null)

const handleMove = (e) => {
    const rect = imageRef.value.getBoundingClientRect()
    const x = e.clientX - rect.left
    const y = e.clientY - rect.top

    const rotateY = ((x / rect.width) - 0.5) * 10
    const rotateX = ((y / rect.height) - 0.5) * -10

    gsap.to(imageRef.value, {
        rotateX,
        rotateY,
        scale: 1.03,
        duration: 0.4,
        ease: "power2.out",
        transformPerspective: 800
    })
}

const resetTilt = () => {
    gsap.to(imageRef.value, {
        rotateX: 0,
        rotateY: 0,
        scale: 1,
        duration: 0.6,
        ease: "power3.out"
    })
}
</script>
  
<style scoped>
.hero {
    min-height: 100vh;
    width: 100%;
    background: #000;
    display: flex;
    align-items: center;
}

.hero-wrapper {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 80px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 60px;
}

/* LEFT SIDE */
.hero-text {
    flex: 1;
    color: white;
}

.hero-text h1 {
    font-size: 64px;
    font-weight: 600;
    color: #ffffff;
    margin-bottom: 20px;
}

.subtitle {
    font-size: 20px;
    color: rgba(255, 255, 255, 0.8);
    margin-bottom: 10px;
}

.tech {
    font-size: 16px;
    color: rgba(255, 255, 255, 0.5);
}

/* RIGHT SIDE */
.hero-image {
    flex: 1;
    display: flex;
    justify-content: center;
}

.image-wrapper {
    perspective: 1000px;
}

.image-wrapper img {
    width: 420px;
    height: 420px;
    object-fit: cover;
    border-radius: 28px;
    transition: box-shadow 0.4s ease;
    box-shadow: 0 40px 80px rgba(0, 0, 0, 0.5);
}

/* RESPONSIVE */
@media (max-width: 900px) {
    .hero-wrapper {
        flex-direction: column;
        text-align: center;
        padding: 40px 20px;
    }

    .hero-image {
        margin-top: 40px;
    }

    .blob-wrapper {
        width: 260px;
        height: 260px;
    }

    .blob-wrapper img {
        width: 220px;
        height: 220px;
    }

    .hero-text h1 {
        font-size: 42px;
    }
}
</style>