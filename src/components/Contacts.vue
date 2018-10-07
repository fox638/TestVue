<template lang="pug">
    section.contacts
        header.contacts__header
            h2.contacts__title Contacts
        .contacts__wrapper
            .contacts__headquarters.headquarter
                h3.headquarter__title GMS
                    span  Headquarters
                .headquarter__wrapper
                    .headquarter__block
                        ul.headquarter__addres-list
                            li.headquarter__addres-item Global Message Services Ukraine LLC
                            li.headquarter__addres-item Bundesstrasse 5 | 3rd Floor
                            li.headquarter__addres-item 6300 Zug
                            li.headquarter__addres-item Switzerland
                        a.headquarter__phone(href="tel:+41415446200") +41 41 544 62 00
                    .headquarter__block
                        dl
                            dt.headquarter__description Email
                            dd
                                a.headquarter__link(href="mailto:info@gms-worldwide.com") info@gms-worldwide.com
                            dt.headquarter__description Send message
                            dd
                                a.headquarter__link(title="Viber" href="viber://chat?number=+41415446200") Vider Us
                            dt.headquarter__description Send form
                            dd
                                a.headquarter__link(href="#") Contact us
            .contacts__technical-support.technical-support
                .technical-support__header
                    .technical-support__title Technical support
                        span  24/7
                .technical-support__wrapper
                    .technical-support__note
                        p GMS understands that it can be hard to follow all new technologies. We regularly provide for all our clients educational trainings to make your operator`s business earn more and better though our best practices.
                    a.technical-support__phone(href="tel:+41415446200") +41 41 544 62 00
</template>

<script>
export default {
}
</script>

<style lang="scss">
</style>
