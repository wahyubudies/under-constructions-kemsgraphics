<script>
    import SOSMED from "../ui-config/sosmed.json";

    let lineKemsTop = "./img/kemsgraphics-line-top.svg";
    let lineKemsBottom = "./img/kemsgraphics-line-bottom.svg";
    let underConstruction = "./img/under-constructions.svg";
    let backLogoRight = "./img/bg-logo-black.svg";
    let backLogoLeft = "./img/bg-logo-black.svg";
    let arrow = "./img/arrow.svg";
    let square = "./img/square.svg";

    let kemsLogoBlack = "./img/black-logo-kems.svg";
    let kemsLogoWhite = "./img/white-logo-kems.svg";
    let logoKems = kemsLogoWhite;

    let isHover = false;
    let sosmedSrcValue = "";

    const handleBlackLogo = () => {
        logoKems = kemsLogoBlack;
    };
    const handleWhiteLogo = () => {
        logoKems = kemsLogoWhite;
    };

    const handleOutlineHover = (item) => {
        isHover = true;
        sosmedSrcValue = item.imageOutline;
    };

    const handleSolidHover = () => {
        isHover = false;
        sosmedSrcValue = "";
    };

    const getSosmedSrc = (sosmed) => {
        if (isHover) {
            return sosmedSrcValue;
        }
        return sosmed.imageSolid;
    };
</script>

<main>
    <!-- konten tengah -->
    <div class="wrapper-content">
        <img src={underConstruction} alt="" class="main-message" />
        <img
            class="logo-kemsgraphics-mobile"
            src={logoKems}
            alt="logo kemsgraphics"
            on:mouseenter={handleBlackLogo}
            on:mouseleave={handleWhiteLogo}
        />
        <div class="wrapper-sosmed">
            <h4>
                But you can get in <br /> touch with us here:
            </h4>
            <div class="sosmed-list">
                {#each SOSMED as smd (smd.name)}
                    <!-- svelte-ignore security-anchor-rel-noreferrer -->
                    <a
                        href={smd.direct}
                        target="_blank"
                        on:mouseenter={() => handleOutlineHover(smd)}
                        on:mouseleave={() => handleSolidHover(smd)}
                    >
                        <img
                            src={smd.imageOutline === sosmedSrcValue
                                ? sosmedSrcValue
                                : smd.imageSolid}
                            alt={smd.name}
                        />
                    </a>
                {/each}
            </div>
        </div>
        <img
            class="logo-kemsgraphics"
            src={logoKems}
            alt="logo kemsgraphics"
            on:mouseenter={handleBlackLogo}
            on:mouseleave={handleWhiteLogo}
        />
    </div>

    <!-- ornamen panah -->
    <div class="wrapper-arrow">
        <img src={arrow} alt="" />
        <div class="copyright">
            <p>kemsgraphics &copy; 2022</p>
            <img src={arrow} alt="" />
        </div>
    </div>

    <!-- police line kemsgraphics -->
    <!-- <img src={lineKemsTop} alt="" class="line line-top" />
    <img src={lineKemsBottom} alt="" class="line line-bottom" /> -->

    <!-- logo bayangan item -->
    <img src={backLogoRight} alt="" class="back-logo logo-right" />
    <img src={backLogoLeft} alt="" class="back-logo logo-left" />

    <!-- ornamen kotak -->
    <img src={square} alt="" class="square-image square-b-l" />
    <img src={square} alt="" class="square-image square-t-r" />
    <img src={square} alt="" class="square-image square-t-l" />
    <img src={square} alt="" class="square-image square-b-r" />
</main>

<style src="./style.sass"></style>
