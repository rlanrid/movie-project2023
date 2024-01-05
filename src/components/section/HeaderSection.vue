<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1><a href="/">Movie Site</a></h1>
            </div>
            <div class="header__intro"
                style="backgroundImage:url(https://image.tmdb.org/t/p/w500/yOm993lsJyPmBodlYjgpPwBjXP9.jpg)">
                <div class="container">
                    <div class="left play__icon">
                        <img src="https://image.tmdb.org/t/p/w500/g5mGMbiZLvgEf628D60GQrPHFJC.jpg" alt="영화포스터">
                    </div>
                    <div class="right">
                        <div class="title">웡카</div>
                        <div class="info">
                            <p class="date">2023-12-06</p>
                            <p class="vote">7.128</p>
                        </div>
                        <p class="desc">
                            마법사이자 초콜릿 메이커 ‘윌리 웡카’의 꿈은 디저트의 성지, ‘달콤 백화점’에 자신만의 초콜릿 가게를 여는 것. 가진 것이라고는 낡은 모자 가득한 꿈과 단돈 12소베른
                            뿐이지만 특별한 마법의 초콜릿으로 사람들을 사로잡을 자신이 있다. 하지만 먹을 것도, 잠잘 곳도, 의지할 사람도 없는 상황 속에서 낡은 여인숙에 머물게 된 ‘웡카’는
                            ‘스크러빗 부인’과 ‘블리처’의 계략에 빠져 눈더미처럼 불어난 숙박비로 인해 순식간에 빚더미에 오른다. 게다가 밤마다 초콜릿을 훔쳐가는 작은 도둑 ‘움파 룸파’의 등장과
                            ‘달콤 백화점’을 독점한 초콜릿 카르텔의 강력한 견제까지. 세계 최고의 초콜릿 메이커가 되는 길은 험난하기만 한데…
                        </p>
                        <div class="credits">
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500//BE2sdjpgsa2rNTFa66f7upkaOP.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500//6v4eEtJnkQIp53hH9csuAJgzvkP.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500//lOkSxsLHHr8DqaE6NylUxwwJZvz.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500//tUHkXYdwm405DjBm2IpPxGjYkjj.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500//n8kf0aowLTcPSt72k0eC4ZShe3s.jpgf" alt="">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<style lang="scss">
.header__inner {
    .header__nav {
        display: flex;
        align-items: center;
        justify-content: space-between;

        h1 {
            font-size: 28px;
            padding: 10px;
            margin: 10px;
            border: 1px solid var(--black);
            display: inline-block;
            font-weight: 800;
            text-transform: uppercase;
            font-family: 'Anton';
            cursor: pointer;
        }
    }

    .header__intro {
        display: flex;
        align-items: center;
        justify-content: center;

        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            z-index: 10;

            @media(max-width: 780px) {
                margin: 0;
                flex-direction: column;
                padding-top: 30px;
            }

            .left {
                width: 20vw;
                min-width: 275px;
            }

            .right {
                width: calc(100% - 40vw);
                margin-left: 2%;

                @media(max-width: 780px) {
                    margin-top: 5vw;
                    width: 100%;
                }

                .info {
                    margin-bottom: 2vw;
                    display: flex;

                    p {
                        &:first-child {
                            position: relative;

                            &::after {
                                content: '';
                                position: absolute;
                                width: 1px;
                                height: 22px;
                                right: -7.5px;
                                top: 0;
                                opacity: 0.9;
                                background-color: var(--white300);

                                @media(max-width:780px) {
                                    height: 17px;
                                }
                            }
                        }

                        &:last-child {
                            margin-left: 14px;
                        }
                    }
                }

                .title {
                    width: 100%;
                    font-size: 3rem;
                    margin-bottom: 10px;
                    line-height: 1;
                    font-weight: 700;
                }

                p {
                    font-size: 16px;

                    @media(max-width:780px) {
                        font-size: 14px;
                    }
                }

                .desc {
                    @mixin line($line) {
                        overflow: hidden;
                        text-overflow: ellipsis;
                        display: -webkit-box;
                        -webkit-line-clamp: $line;
                        -webkit-box-orient: vertical;
                    }

                    margin-bottom: 2vw;
                    @include line(5);
                }

                .credits {
                    display: flex;
                    align-items: center;

                    div {
                        width: 6vw;
                        margin-right: 15px;

                        @media(max-width:780px) {
                            width: 19%;
                        }
                    }
                }
            }
        }

        width: 100%;
        height: 90vh;
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
        position: relative;

        &:before {
            content: '';
            width: 100%;
            height: 100%;
            backdrop-filter: blur(10px);
            filter: brightness(50%);
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
        }
    }
}
</style>