<script setup lang="ts">

import gsap from "gsap";
import {ScrollTrigger} from "gsap/ScrollTrigger";
import Lenis from "lenis";

onMounted((): void => {
    const lenis = new Lenis({
        duration: 2.000,
    });

    const performScrollAnimationFrame = (time: number): void => {
        lenis.raf(time);
        requestAnimationFrame(performScrollAnimationFrame);
    }

    requestAnimationFrame(performScrollAnimationFrame);

    gsap.registerPlugin(ScrollTrigger);

    gsap.to("#hero", {
        keyframes: {
            "70%": {
                alpha: 1.00,
                y: 0,
            },

            "100%": {
                alpha: 0.00,
                y: -100,
            }
        },

        scrollTrigger: {
            trigger: "#hero",
            scrub: true,
        }
    })

    gsap.utils.toArray("h2").forEach(h2 => {
        gsap.from(h2, {
            x: -60,
            alpha: 0,
            duration: 0.800,
            skewX: -50,
            ease: "back.out(1.7)",
            scrollTrigger: {
                trigger: h2,
                toggleActions: "restart none none none",
            }
        });
    });

    gsap.utils.toArray(".feedback__feedback:nth-child(2n + 0)").forEach(feedback => {
        gsap.from(feedback, {
            x: -60,
            ease: "back.out(1.7)",
            duration: 0.800,
            scrollTrigger: {
                trigger: feedback,
                toggleActions: "restart none restart none",
                scrub: true,
            }
        })
    });

    gsap.utils.toArray(".feedback__feedback:nth-child(2n + 1)").forEach(feedback => {
        gsap.from(feedback, {
            x: 60,
            ease: "back.out(1.7)",
            duration: 0.800,
            scrollTrigger: {
                trigger: feedback,
                toggleActions: "restart none restart none",
                scrub: true,
            }
        })
    });

    gsap.from("#photos__head-photo-image", {
        x: 100,
        alpha: 0,
        duration: 1.200,
        ease: "power1.out",
        scrollTrigger: {
            trigger: "#photos__head-photo-image",
            toggleActions: "restart none restart none",
        }
    });

    gsap.to("#photos__grid", {
        keyframes: {
            "0%": {
                transform: "scale(1.03)",
            },

            "50%": {
                transform: "scale(1)",
            },

            "100%": {
                transform: "scale(1.03)",
            },
        },

        scrollTrigger: {
            trigger: "#photos__grid",
            scrub: true,
        }
    });

    gsap.utils.toArray(".features__feature").forEach(feature => {
        gsap.from(feature, {
            y: 60,
            ease: "back.out(1.7)",
            duration: 0.800,
            scrollTrigger: {
                trigger: feature,
                toggleActions: "restart none restart none",
            }
        })
    });

    gsap.from(".prices__card:nth-child(1)", {
        x: -60,
        rotate: -30,
        duration: 1.500,
        alpha: 0,
        transform: "scale(0.8)",
        ease: "elastic.out",
        scrollTrigger: {
            trigger: ".prices__card:nth-child(1)",
            toggleActions: "restart none none none",
        }
    });

    gsap.from(".prices__card:nth-child(2)", {
        x: 60,
        rotate: 5,
        duration: 1.500,
        delay: 0.200,
        alpha: 0,
        transform: "scale(0.8)",
        ease: "elastic.out",
        scrollTrigger: {
            trigger: ".prices__card:nth-child(2)",
            toggleActions: "restart none none none",
        }
    });

    gsap.from(".prices__card:nth-child(3)", {
        rotate: -7,
        duration: 1.800,
        delay: 0.300,
        alpha: 0,
        transform: "scale(0.9)",
        ease: "elastic.out",
        scrollTrigger: {
            trigger: ".prices__card:nth-child(3)",
            toggleActions: "restart none none none",
        }
    });
});
</script>

<template>
    <div id="dragon-nest">
        <section id="hero">
            <img src="/images/hero-full.png" alt="Dragon Nest" id="hero__image">
        </section>

        <section id="events">
            <h2 id="events__heading">Ближайшие события</h2>
            <div id="events__cards">
                <a href="https://vk.com/@gnesvdk-tarify?anchor=snyat-vs-pomeschenie-dlya-prazdnikov-ili-krupnykh-meropriaty" class="events__card">
                    <img class="events__card-image" src="/images/event-1.jpg" alt="">

                    <p class="events__card-description">
                        Проведи тут своё день рождение или лекцию
                    </p>
                </a>

                <a href="https://vk.com/@gnesvdk-gotovoe-mesto-dlya-rolevyh-igr" class="events__card">
                    <img class="events__card-image" src="/images/event-2.jpg" alt="">

                    <p class="events__card-description">
                        "Подземелья и драконы", бункер, караоке и другие развлечения
                    </p>
                </a>

                <a href="https://t.me/gnesvdk" class="events__card">
                    <img class="events__card-image" src="/images/event-3.jpg" alt="">

                    <p class="events__card-description">
                        Мафия, квартирники, игротеки и кинопоказы каждую неделю
                    </p>
                </a>
            </div>
        </section>

        <section id="photos">
            <div id="photos__head">
                <img src="/images/dragon-nest.png" alt="" id="photos__head-nest-image">
                <h2 id="photos__heading">Фото гнезда</h2>
                <img src="/images/dragon-taking-photos.png" alt="" id="photos__head-photo-image">
            </div>

            <div id="photos__grid">
                <div class="photos__grid-photo-container">
                    <img src="/images/photo-1.jpg" alt="" class="photos__grid-photo">
                </div>

                <div class="photos__grid-photo-container">
                    <img src="/images/photo-2.jpg" alt="" class="photos__grid-photo">
                </div>

                <div class="photos__grid-photo-container">
                    <img src="/images/photo-3.jpg" alt="" class="photos__grid-photo">
                </div>

                <div class="photos__grid-photo-container">
                    <img src="/images/photo-4.jpg" alt="" class="photos__grid-photo">
                </div>
            </div>
        </section>

        <section id="features">
            <h2 id="features__heading">О нашем уютном гнёздышке</h2>

            <div id="features__grid">
                <div class="features__feature">
                    <img src="/images/dragon-with-a-circle.png" alt="dragon-with-a-circle" class="features__feature-image">
                    <h3 class="features__feature-name">
                        Находимся на первой речке. Железнодорожный переулок 3.
                    </h3>
                </div>

                <div class="features__feature">
                    <img src="/images/dragon-nest-area.png" alt="dragon-nest-area" class="features__feature-image">
                    <h3 class="features__feature-name">
                        20 м2. Уютная комната.<br>
                        До 16 посадочных мест
                    </h3>
                </div>

                <div class="features__feature">
                    <img src="/images/dragon-projector.png" alt="dragon-projector" class="features__feature-image">
                    <h3 class="features__feature-name">Большой зал и проектор</h3>
                </div>

                <div class="features__feature">
                    <img src="/images/dragon-drinking-tea.png" alt="dragon-drinking-tea" class="features__feature-image">
                    <h3 class="features__feature-name">Вкуснейшие напитки</h3>
                </div>

                <div class="features__feature">
                    <img src="/images/dragon-sitting-in-a-tower.png" alt="dragon-sitting-in-a-tower" class="features__feature-image">
                </div>
            </div>
        </section>

        <section id="prices">
            <h2 id="prices__heading">Аренда залов</h2>

            <div id="prices__grid">
                <div class="prices__card">
                    <img src="/images/dragon-throwing-dices-and-pizza.png" alt="" class="prices__card-image">

                    <h3 class="prices__card-heading">Будни</h3>
                    <p class="prices__card-description">
                        1 час = 700 руб
                    </p>

                    <a href="https://t.me/gnezdo_ls" class="prices__card-button">Арендовать</a>
                </div>

                <div class="prices__card">
                    <img src="/images/dragon-in-a-party-hat.png" alt="" class="prices__card-image">

                    <h3 class="prices__card-heading">Выходные</h3>
                    <p class="prices__card-description">
                        1 час = 500 руб
                    </p>

                    <a href="https://t.me/gnezdo_ls" class="prices__card-button">Арендовать</a>
                </div>

                <div class="prices__card">
                    <h3 class="prices__card-heading">Заказать ведущего</h3>
                    <div class="prices__card-week-day-line">
                        <span class="prices__card-week-day">Ведущий мафии</span>
                        <span class="prices__card-week-day-price">1 человек = 700 руб</span>
                    </div>

                    <div class="prices__card-week-day-line">
                        <span class="prices__card-week-day">Ведущий D&D</span>
                        <span class="prices__card-week-day-price">1 человек = 1300 руб</span>
                    </div>

                    <a href="https://t.me/gnezdo_ls" class="prices__card-button">Заказать</a>
                </div>
            </div>
        </section>

        <section id="contacts">
            <a href="https://t.me/gnesvdk" class="contacts__contact">
                <img src="/images/telegram.png" alt="" class="contacts__contact-image">
                <span class="contacts__contact-text">Наш ТГ</span>
            </a>

            <a href="https://vk.com/gnesvdk" class="contacts__contact">
                <img src="/images/vk.png" alt="" class="contacts__contact-image">
                <span class="contacts__contact-text">Наш ВК</span>
            </a>

            <a href="https://api.whatsapp.com/send?phone=79952805379" class="contacts__contact">
                <img src="/images/whatsapp.png" alt="" class="contacts__contact-image">
                <span class="contacts__contact-text">Наш WA</span>
            </a>

            <a href="tel:+7995-280-53-79" class="contacts__contact">
                <img src="/images/phone.png" alt="" class="contacts__contact-image">
                <span class="contacts__contact-text">+79952805379</span>
            </a>
        </section>

        <section id="map">
            <div id="map__map" style="position:relative;overflow:hidden;"><a href="https://yandex.ru/maps/org/gnezdo_drakona/142273186236/?utm_medium=mapframe&utm_source=maps" style="color:#eee;font-size:12px;position:absolute;top:0px;">Гнездо Дракона</a><a href="https://yandex.ru/maps/75/vladivostok/category/board_games/184107267/?utm_medium=mapframe&utm_source=maps" style="color:#eee;font-size:12px;position:absolute;top:14px;">Настольные и интеллектуальные игры во Владивостоке</a><a href="https://yandex.ru/maps/75/vladivostok/category/anti_caf_/31370163603/?utm_medium=mapframe&utm_source=maps" style="color:#eee;font-size:12px;position:absolute;top:28px;">Антикафе во Владивостоке</a><iframe src="https://yandex.ru/map-widget/v1/?from=mapframe&ll=131.920697%2C43.130923&mode=search&oid=142273186236&ol=biz&z=14.47" width="560" height="400" frameborder="1" allowfullscreen="true" style="position:relative;width:100%;height:100%;"></iframe></div>
        </section>

        <section id="feedback">
            <h2 id="feedback__heading">Отзывы</h2>

            <div id="feedback__grid">
                <div class="feedback__feedback">
                    <img src="/images/dragon-circle-staring.png" alt="" class="feedback__feedback-image">
                    <p class="feedback__feedback-text">
                        Суперкомфортик<br />
                        Очень крутые ребята работают и интересно можно провести время
                    </p>
                </div>

                <div class="feedback__feedback">
                    <img src="/images/dragon-circle-idle.png" alt="" class="feedback__feedback-image">
                    <p class="feedback__feedback-text">
                        Хочу выразить благодарность ребятам. Провели веселый вечер, а главное комфортный. Вячеслав мастер своего дела. Вы большие молодцы. Советую всем посетить это место
                    </p>
                </div>

                <div class="feedback__feedback">
                    <img src="/images/dragon-circle-excited.png" alt="" class="feedback__feedback-image">
                    <p class="feedback__feedback-text">
                        Большое разнообразие игры, добрые, весёлые и интересные админы) Вкусный чай и клёвая атмосфера! Музыка просто огонь! Советую посетить данное антикафе
                    </p>
                </div>

                <div class="feedback__feedback">
                    <img src="/images/dragon-circle-kissing.png" alt="" class="feedback__feedback-image">
                    <p class="feedback__feedback-text">
                        Очень хорошее место, большая коллекция настольных игр на любой вкус и любую компанию. Ребята часто проводят мероприятия на которые очень легко записаться (быстро отвечают в группе) и в общем крутая атмосфера и дружеское отношение к клиентам
                    </p>
                </div>
            </div>

            <img src="/images/fire.png" alt="" id="feedback__background-image">
        </section>
    </div>
</template>

<style scoped lang="sass">
@use 'sass:color'

$berries: #3D0832
$vine: #5D1934
$blood: #892B38
$fire: #9D4B2D
$peach: #FF9C64
$sand: #FFD5AE
$strawberry-cocktail: #BC5B64
$chair: #90466A
$lava: #FF9028
$snow: #FFFFFF
$magma: #F19152
$wood: #EFB37E
$pyramid: #FFCE97
$coal: #000000
$dragon-gradient: linear-gradient(to bottom, $berries 0%, $blood 20%, $fire 55%, $blood 90%)

#dragon-nest
    background-image: $dragon-gradient
    contain: paint

*, *::before, *::after
    box-sizing: border-box
    font-family: "Avdira", serif
    color: $snow

*::selection
    background: #77777733

img
    object-fit: cover

section
    max-width: 100lvw

h1, h2, h3, h4, h5, h6
    margin: 0

h2
    font-size: 4rem

#hero
    display: grid
    place-items: center

#hero__image
    width: 100%

#events
    margin-block-start: -11rem
    padding-inline: 6rem

#events__heading
    text-align: right
    padding-inline-end: 2ch

#events__cards
    display: flex
    justify-content: space-between
    column-gap: 6rem
    margin-block-start: 3rem
    transform-style: preserve-3d
    transform: perspective(1000px)

.events__card
    background: $strawberry-cocktail
    border-radius: 1rem
    contain: paint
    flex: 1
    text-decoration: none
    transition: 350ms cubic-bezier(.31,1.36,.32,.99)

    &:hover
        transform: translateZ(3rem)
        outline: color.adjust($strawberry-cocktail, $alpha: -0.80) 1rem solid
        filter: brightness(120%)

    &:hover + *
        transform: translateZ(2.5rem) rotateY(5deg)
        opacity: 0.4

    &:hover + * + *
        transform: translateZ(-4.5rem) rotateY(15deg)
        opacity: 0.4

    &:has(+ *:hover)
        transform: translateZ(2.5rem) rotateY(-5deg)
        opacity: 0.4

    &:has(+ * + *:hover)
        transform: translateZ(-4.5rem) rotateY(-15deg)
        opacity: 0.4

.events__card-image
    object-fit: cover
    object-position: 20% 50%
    width: 100%
    height: 28rem

.events__card-name
    text-transform: uppercase
    font-size: 3rem

.events__card-description
    font-size: 2rem
    padding-inline: 1rem
    padding-block: 0.5rem
    font-weight: 100

#photos
    margin-block-start: 4rem

#photos__head
    display: flex
    justify-content: space-between
    position: relative

#photos__head-photo-image
    align-self: flex-end

#photos__heading
    position: absolute
    bottom: 6rch
    left: 36rch
    z-index: 10

#photos__head-nest-image
    visibility: hidden

#photos__grid
    display: grid
    grid-template-columns: repeat(3, 1fr)
    z-index: 10

.photos__grid-photo-container
    height: 24rem
    contain: paint

    &:first-child, &:last-child
        grid-column: span 2

.photos__grid-photo
    object-fit: cover
    width: 100%
    height: 100%
    transition: 450ms ease-out

    &:hover
        transition: 150ms ease-out
        transform: scale(1.2)

#features
    padding-inline: 3rem
    margin-block-start: 3rem

#features__heading
    text-align: center

#features__grid
    display: grid
    grid-template-columns: repeat(3, 1fr)
    grid-template-rows: repeat(2, 1fr)
    margin-block: 1rem

.features__feature
    display: grid
    place-items: center

    &:last-child
        grid-column: 3
        grid-row: 1 / span 2

.features__feature-name
    font-size: 2rem
    text-align: center

#feedback__background-image
    width: 100%

#prices
    margin-block-start: 3rem

#prices__heading
    text-align: center

#prices__grid
    display: grid
    grid-template-columns: repeat(2, 1fr)
    padding-inline: 18rem
    grid-gap: 4rem
    margin-block-start: 3rem

.prices__card
    background: $vine
    border-radius: 1rem
    padding-block: 4rem
    padding-inline: 2rem
    position: relative
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center

    &:nth-child(1) .prices__card-image
        left: -229px
        top: -150px

    &:nth-child(2) .prices__card-image
        right: -203px
        top: -120px

    &:last-child
        grid-column: span 2

        .prices__card-button
            margin-block-start: 3rem

.prices__card-image
    position: absolute
    height: 500px

.prices__card-heading
    font-size: 3rem
    color: $peach
    text-align: center

.prices__card-description
    font-size: 2rem
    color: $sand
    text-align: center

.prices__card-button
    background: $magma
    font-size: 2rem
    color: $snow
    border: none
    padding: 0.5rem 1rem
    border-radius: 0.5rem
    font-weight: 1000
    text-decoration: none
    transition: 150ms ease-out

    &:hover
        scale: 1.050
        filter: brightness(120%)

    &:active
        scale: 1.025
        filter: brightness(130%)

.prices__card-week-day-line
    display: flex
    align-items: center
    justify-content: space-between
    font-size: 2rem
    width: max(48ch, 50%)
    margin-block-start: 1rem

    *
        color: $sand

.prices__card-week-day
    display: inline-block
    padding: 0.25em
    background: $chair
    border-radius: 0.5rem
    min-width: 15ch
    width: 18ch
    text-align: center
    text-wrap: nowrap

#contacts
    display: flex
    align-items: center
    justify-content: space-between
    padding-inline: 4rem

.contacts__contact
    display: inline-flex
    flex-direction: column
    text-decoration: none
    align-items: center
    justify-content: space-between
    transition: 150ms ease-out
    user-select: none

    &:nth-child(2n):hover
        rotate: 5deg

    &:nth-child(2n + 1):hover
        rotate: -5deg

    &:nth-child(2n):active
        rotate: 3deg

    &:nth-child(2n + 1):active
        rotate: -3deg

    &:hover
        scale: 1.05

    &:active
        scale: 1.025

.contacts__contact-image
    width: 100%

.contacts__contact-text
    font-size: 1.75rem
    color: $sand
    font-weight: 1000

#map
    margin-block-start: 4rem

#map__map
    height: 80lvh

#feedback
    position: relative
    isolation: isolate
    min-height: 140lvh
    margin-block-start: 4rem
    display: flex
    align-items: center
    justify-content: center
    flex-direction: column
    row-gap: 3rem

#feedback__heading
    text-align: center

#feedback__grid
    display: grid
    grid-template-columns: repeat(2, 1fr)
    padding-inline: 6rem
    grid-gap: 6rem

.feedback__feedback
    display: flex
    gap: 1.5rem
    align-items: flex-end

    &:nth-child(4n + 0)
        flex-direction: column
        align-items: flex-start

    &:nth-child(4n + 1)
        flex-direction: row

    &:nth-child(4n + 2)
        flex-direction: column-reverse

    &:nth-child(4n + 3)
        flex-direction: row-reverse
        align-items: flex-start

.feedback__feedback-image
    width: 4rem
    height: 4rem

.feedback__feedback-text
    background: $pyramid
    color: $coal
    padding: 1.5rem
    border-radius: 1rem
    font-size: 1.5rem
    margin: 0
    max-width: 36ch

#feedback__background-image
    position: absolute
    bottom: 0
    left: 0
    right: 0
    z-index: -1

@media screen and (max-width: 1500px)
    #events
        margin-block-start: 0

    #events__heading
        padding-inline-end: 0
        text-align: center

    #events__cards
        flex-direction: column
        row-gap: 4rem
        padding-inline: min(10dvw, 16rem)

    .events__card
        &:hover + *, &:hover + * + *, &:has(+ *:hover), &:has(+ * + *:hover)
            transform: initial
            opacity: initial

    #photos__head
        margin-block-start: 18rem

    #photos__head-nest-image
        display: none

    #photos__heading
        position: initial
        margin-inline-start: 4rem
        margin-block-start: auto
        margin-block-end: 2rem

    #photos__head-photo-image
        max-width: 70dvw
        position: absolute
        bottom: 0
        right: 0

    #features__grid
        grid-template-columns: repeat(2, 1fr)
        grid-template-rows: repeat(2, 1fr)

    .features__feature:last-child
        display: none

    #prices__grid
        display: flex
        flex-direction: column

    .prices__card:nth-child(1) .prices__card-image
        top: -75px

    .prices__card:nth-child(2) .prices__card-image
        top: -55px

    .prices__card:last-child
        grid-column: span 1


@media screen and (max-width: 1325px)
    .prices__card-week-day-line
        flex-direction: column
        margin-block-start: 3rem
        row-gap: 0.5rem

    #contacts
        display: grid
        grid-template-rows: repeat(2, 1fr)
        grid-template-columns: repeat(2, 1fr)


@media screen and (max-width: 1000px)
    #events__cards
        padding-inline: 1rem

    #photos__heading
        text-align: center

    #photos__grid
        grid-template-rows: repeat(4, 1fr)
        grid-template-columns: 1fr

    .photos__grid-photo-container
        grid-column: span 1 !important

    #features__grid
        margin-block-start: 2.5rem

    #feedback__grid
        grid-template-columns: 1fr
        grid-template-rows: initial
        padding-block: 4rem


@media screen and (max-width: 900px)
    #features__grid
        grid-template-rows: repeat(1, 4fr)
        grid-template-columns: 1fr
        row-gap: 2rem

    #prices__grid
        padding-inline: 12rem

    .prices__card-image
        height: 300px

    .features__feature-image
        max-width: 100%

    .prices__card:nth-child(1) .prices__card-image
        top: 0
        left: -140px

    .prices__card:nth-child(2) .prices__card-image
        top: 55px
        right: -122px


@media screen and (max-width: 800px)
    #prices__grid
        padding-inline: 4rem

    .prices__card
        contain: paint

    .prices__card-image
        opacity: 0.20
        bottom: 0
        top: initial
        height: 350px

    .prices__card:nth-child(1) .prices__card-image
        left: initial
        right: -110px

    .prices__card:nth-child(2) .prices__card-image
        right: initial
        left: -50px
        transform: rotate(22.5deg)
        top: 20px

    #feedback__grid
        padding-inline: 2rem


@media screen and (max-width: 700px)
    h2
        font-size: 2.5rem

    #events__heading
        margin-block-start: 4rem

    .events__card-name
        font-size: 2.25rem

    .events__card-description
        font-size: 1.5rem

    .prices__card
        padding-inline: 2rem

    .prices__card-heading
        font-size: 2.25rem

    .prices__card-description, .prices__card-week-day, .prices__card-week-day-price
        font-size: 1.75rem

    .prices__card-button
        font-size: 1.5rem

@media screen and (max-width: 600px)
    #photos__head-photo-image
        display: none

    #events
        padding-inline: 2rem

    #prices__grid
        padding-inline: 2rem

    #contacts
        grid-template-columns: 1fr
        grid-template-rows: initial

    .feedback__feedback-text
        max-width: initial

    .feedback__feedback-image
        display: none

// -- Font Faces Are Below --
@font-face
    font-family: "Avdira"
    src: url("/fonts/Avdira_R.otf")
    font-weight: 500

@font-face
    font-family: "Avdira"
    src: url("/fonts/Avdira_B.otf")
    font-weight: 700

</style>