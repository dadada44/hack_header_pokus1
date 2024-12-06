<script>
    // Stav pro toggle mobilního menu
    let isMenuOpen = false;
  
    // Navigační odkazy
    let links = [
      { name: "Home", href: "/" },
      { name: "About", href: "/about" },
      { name: "Services", href: "/services" },
      { name: "Contact", href: "/contact" },
    ];
</script>
  
<header>
    <div class="container">
        <img src="/img/logo.png" alt="">
  
      <!-- Hamburger Button -->
        <button class="hamburger" on:click={() => (isMenuOpen = !isMenuOpen)} aria-expanded={isMenuOpen}>
            <div class="line top" class:isOpen={isMenuOpen}></div>
            <div class="line middle" class:isOpen={isMenuOpen}></div>
            <div class="line bottom" class:isOpen={isMenuOpen}></div>
        </button>
  
      <!-- Navigační menu -->
        <div class="menu-overlay" class:isOpen={isMenuOpen}>
            <nav class="menu">
                {#each links as { name, href }}
                    <a href={href} on:click={() => (isMenuOpen = false)}>{name}</a>
                {/each}
            </nav>
        </div>
    </div>
</header>
  
<style lang="scss">
    header {
    height: 100px;
    margin: 0;
    padding: 0;
    background-color: #9f7878;

        .container {
            max-width: 1300px;
            margin: auto;
            display: flex;
            justify-content: space-between;
            height: 100px;
            align-items: center;

            .logo {
            height: 100%;
            display: flex;
            justify-content: center;
            align-content: center;

                img {
                    width: 100px;
                }
            }
        }
    }

    .hamburger {
    display: flex;
    flex-direction: column;
    gap: 6px;
    background: none;
    border: none;
    cursor: pointer;
    position: relative;
    z-index: 50;

        .line {
            width: 30px;
            height: 3px;
            border-radius: 30px;
            background-color: #333;
            transition: all 0.8s cubic-bezier(0.23, 1, 0.32, 1);

            &.top.isOpen {
            transform: translateY(9px) rotate(90deg);
            background-color: #ff88df;
            }

            &.middle.isOpen {
            transform: scaleX(0);
            opacity: 0%;
            }

            &.bottom.isOpen {
            transform: translateY(-9px) translateX(-10px) rotate(-90deg);
            }
        }
    }

    .menu-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(176, 101, 101, 0.9);
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transform: scale(0.95);
    transition: transform 0.5s ease, opacity 0.5s ease;
    pointer-events: none;

        &.isOpen {
            opacity: 1;
            transform: scale(1);
            pointer-events: all;
            
        }

        .menu {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            text-align: center;

            a {
            color: #fff;
            font-size: 1.5rem;
            text-decoration: none;
            transition: color 0.3s ease;

                &:hover {
                    color: #0070f3;
                }
            }
        }
    }

</style>

  