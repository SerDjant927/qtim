<template>
    <!--Тут использовал статичную верстку, т.к такие простые элементы не имеет большого смысла гонять через циклы js-->
    <footer class="footer">
        <div class="container">
            <section class="footer-top">
                <div class="footer-top__block">
                    <span class="footer-top__small-text">Is there a project?</span>
                    <div class="footer-top__main-text">Let’s work<br /> together</div>
                </div>
                <div class="footer-top__block">
                    <ul class="contacts-list">
                        <li class="contacts-list__elem">
                            <span>For all questions</span>
                            <a href="tel:+79202780068">+7 (920) 278—00—68</a>
                            <a href="mailto:qtim@agency.com">qtim@agency.com</a>
                        </li>
                        <li class="contacts-list__elem">
                            <span>Office in Russia</span>
                            <span>139 Ruben Station Lake Drew, NM 52678</span>
                            <svg width="32" height="32" viewBox="0 0 32 32" fill="none"
                                xmlns="http://www.w3.org/2000/svg">
                                <rect width="32" height="32" rx="16" fill="#101010" />
                                <path d="M17.5 20.5L20.5 11.5L11.5 14.5L15.25 16.75L17.5 20.5Z" stroke="#E2BEFF"
                                    stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round" />
                            </svg>
                        </li>
                        <li class="contacts-list__elem">
                            <span>Office in Dubai</span>
                            <span>139 Ruben Station Lake Drew, NM 52678</span>
                            <svg width="32" height="32" viewBox="0 0 32 32" fill="none"
                                xmlns="http://www.w3.org/2000/svg">
                                <rect width="32" height="32" rx="16" fill="#101010" />
                                <path d="M17.5 20.5L20.5 11.5L11.5 14.5L15.25 16.75L17.5 20.5Z" stroke="#E2BEFF"
                                    stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round" />
                            </svg>
                        </li>
                    </ul>
                </div>
            </section>
            <section class="footer-bottom">
                <ul class="footer-links">
                    <li class="footer-links__item">
                        <a class="footer-links__link" href="#">Facebook</a>
                    </li>
                    <li class="footer-links__item">
                        <a class="footer-links__link" href="#">Facebook</a>
                    </li>
                    <li class="footer-links__item">
                        <a class="footer-links__link" href="#">Facebook</a>
                    </li>
                </ul>
                <a class="footer-bottom__btn" href="#">Go</a>
                <ul class="footer-links">
                    <li class="footer-links__item">
                        <a class="footer-links__link" href="#">Behance</a>
                    </li>
                    <li class="footer-links__item">
                        <a class="footer-links__link" href="#">Linkedn</a>
                    </li>
                    <li class="footer-links__item">
                        <a class="footer-links__link" href="#">Privacy Policy</a>
                    </li>
                </ul>
            </section>
        </div>

    </footer>
</template>
<script>
export default {
    name: 'FooterComponent',
}
</script>
<style scoped lang="less">
.footer {
    background-color: #E2BEFF;
    margin-top: 80px;
    padding-top: 80px;
    overflow: hidden;
}

.footer-top {
    display: flex;
    width: 100%;
    align-items: flex-start;
    justify-content: space-between;

    &__small-text {
        color: #101010;
        font-size: 16px;
        font-weight: 400;
        line-height: 19px;
        letter-spacing: 0.01em;
    }

    &__main-text {
        color: #101010;
        font-size: 112px;
        font-weight: 400;
        line-height: 112px;
        margin-top: 56px;
    }
}

.contacts-list {
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    flex-direction: column;
    row-gap: 36px;

    &__elem {
        display: flex;
        flex-direction: column;
        color: #101010;
        row-gap: 12px;
        font-size: 16px;
        font-weight: 400;
        line-height: 19px;
        letter-spacing: 0.01em;

        a {
            color: #101010;
            text-decoration: none;
        }
    }

}

.footer-bottom {
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
    margin-top: 140px;

    &__btn {
        color: #f3f3f3;
        font-size: 32px;
        font-weight: 400;
        line-height: 32px;
        display: flex;
        align-items: center;
        justify-content: center;
        text-decoration: none;
        padding: 122px 122px 40px;
        position: relative;
        z-index: 2;

        &::before {
            z-index: -1;
            content: '';
            position: absolute;
            height: 440px;
            width: 440px;
            border-radius: 100%;
            overflow: hidden;
            background-color: #101010;
        }

        &:hover {
            &::before {
                -webkit-box-shadow: 0px 0px 24px 14px rgba(34, 60, 80, 0.2);
                -moz-box-shadow: 0px 0px 24px 14px rgba(34, 60, 80, 0.2);
                box-shadow: 0px 0px 24px 14px rgba(34, 60, 80, 0.2);
            }
        }
    }
}

.footer-links {
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    column-gap: 32px;
    padding: 40px 0;

    &__link {
        color: #101010;
        font-size: 16px;
        font-weight: 400;
        line-height: 19px;
        letter-spacing: 0.01em;
    }
}
</style>