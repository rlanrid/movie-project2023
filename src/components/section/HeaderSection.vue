<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1>Movie Site</h1>
                <nav>
                    <ul>
                        <li><a href="#">공포 영화 TOP10</a></li>
                        <li><a href="#">슬픈 영화 TOP10</a></li>
                    </ul>
                </nav>
            </div>
            <div class="header__intro"
                style="backgroundImage:url(https://image.tmdb.org/t/p/w500/dZbLqRjjiiNCpTYzhzL2NMvz4J0.jpg)">
                <div class="container">
                    <div class="left">
                        <img src="https://image.tmdb.org/t/p/w500/bvwEkotIuHxjuSCEXhhSna0BqQT.jpg" alt="영화포스터">
                    </div>
                    <div class="right">
                        <h2>쏘우X</h2>
                        <p class="desc">
                            존은 암을 치료할 수 있는 기적을 기대하며 위험하고 실험적인 의료 시술을 받기 위해 멕시코로 떠났지만,
                            이 모든 수술이 가장 취약한 사람들을 속이기 위한 사기라는 사실을 알게 된다.
                        </p>
                        <div class="info">
                            <p class="date">출시 : 2023-09-26</p>
                            <p class="vote">평점 : 7.401</p>
                        </div>
                        <div class="credits">
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/q21uuCtTioIVcGc3a1Q0DpdcNMO.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/s2Ouz4b7xqDH72aU48TSW5zS40v.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/a5r4MtoL5jU4DtCp0BtzwEAtfyL.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/oWkitw5jzILwb775CVGjsqMSrqz.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/9lEbP0scP8vjNa4hYmAg4UgMQky.jpg" alt="">
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

        nav {
            ul {
                padding-right: 10px;
            }

            li {
                display: inline;

                a {
                    display: inline-block;
                    padding: 10px 20px;
                    border: 1px solid var(--white);
                    margin-left: 10px;
                    transition: all 0.3s;

                    &:hover {
                        background-color: var(--white);
                        color: var(--black);
                    }
                }
            }
        }
    }

    .header__intro {
        .container {
            display: flex;
            justify-content: space-between;
            padding-top: 100px;
            position: relative;
            z-index: 10;

            .left {
                width: 350px;
            }

            .right {
                width: calc(100% - 350px);
                margin-left: 2%;
                display: flex;
                flex-direction: column;
                justify-content: space-between;

                h2 {
                    font-size: 26px;
                    margin-bottom: 10px;
                }

                p {
                    font-size: 16px;
                }

                .desc {
                    margin-bottom: 10px;
                }

                .credits {
                    display: flex;
                    align-items: center;

                    div {
                        width: 150px;
                        margin-right: 15px;
                    }
                }
            }
        }

        width: 100%;
        height: 700px;
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