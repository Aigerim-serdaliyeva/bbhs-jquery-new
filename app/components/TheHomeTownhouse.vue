<template lang="pug">

-
    var info = [
        {
            title: '1-ой очереди',
            text: ''
        }, 
        {
            title: '2-ой очереди',
            text: ''
        }
    ]

.home-townhouse            
    .home-townhouse__wrap.desk-container
        .home-townhouse__content.desk
            each item in info
                .home-townhouse__text
                    article
                        h2.phen-700 ТАУНХАУСЫ 
                        h2.phen-700 !{item.title}
                        p.phen-300 !{item.text}
        .home-townhouse__layout
            img.desk(src="@/assets/images/desktop/home-townhouse-layout.png", alt="")
            img.mob(src="@/assets/images/mobile/home-townhouse-layout.png", alt="")
        actions.desk
    .home-townhouse__descr.desk.phen-700(v-if='descr' :class='descrText' :style='descrStyle')
        | {{descrText}}

</template>

<script>
import actions from "@/components/TheHomeTownhouseActions";
import { mapGetters } from "vuex";

export default {
    components: {
        actions
    },
    computed: {
        ...mapGetters({
            descr: "townhouse/descr",
            descrText: "townhouse/descrText",
            descrStyle: "townhouse/descrStyle"
        })
    }
};
</script>

<style lang="scss">
.home-townhouse {
    position: relative;
    &__wrap {
        position: relative;
    }
    &__layout {
        img {
            display: block;
            margin: auto;
        }
    }
    &__content {
        position: absolute;
        top: rem(220);
        left: 0;
        width: 100%;
    }
    &__text {
        width: 100%;
        &:first-child {
            @include flex(flex-end, center);
            article {
                margin-right: rem(20);
            }
        }
        &:last-child {
            @include flex(flex-start, center);
            position: relative;
            top: rem(130);
            text-align: right;
            article {
                margin-left: rem(15);
            }
        }
        article {
            h2 {
                @include fonted(rem(48), rem(48));
                margin-bottom: rem(9);
            }
            p {
                font-size: rem(24);
            }
        }
    }
}

@media #{$desktop} {
    .home-townhouse {
        &__descr {
            position: absolute;
            pointer-events: none;
            top: 0;
            left: 0;
            background: #39071f;
            border: 3px solid #ffffff;
            padding: rem(31) rem(37);
            font-size: rem(24);
            text-transform: uppercase;
        }
    }
}
</style>
