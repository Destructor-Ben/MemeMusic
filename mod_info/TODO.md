# To Do List

- Convert icon to a png and use the automatic DDS conversion

- Make mod icon and album icon
- Make sure the mod is working properly
- Add different chances to the songs and make them play at appropriate times
- Adjust volumes
- Trim nig nig nay nay
- Trim gangnam style

[20:47:18][no_game_date][pdx_audiomusic_sdl.cpp:76]: For best performance and quality music files should be in 44.1kHz (MM_inter_ndns)
[20:47:19][no_game_date][pdx_audiomusic_sdl.cpp:76]: For best performance and quality music files should be in 44.1kHz (MM_inter_hava_nagila)
[20:47:19][no_game_date][pdx_audiomusic_sdl.cpp:76]: For best performance and quality music files should be in 44.1kHz (MM_inter_gangnam_style)


# TODO: simplify
music = {
    song = "MM_napoleon"
    chance = {
        base = 0

        # Only make it play during war if someone is losing
        modifier = {
            add = 1
            has_war = yes

            OR = {
                surrender_progress > 10

                any_country = {
                    AND = {
                        has_war_with = ROOT
                        surrender_progress > 10
                    }
                }
            }
        }

        # Boost chance if we are France or at war with them
        modifier = {
            factor = 2
            
            OR = {
                TAG = FRA
                has_war_with = FRA
            }
        }

        # Boost chance if we are losing
        modifier = {
            set_temp_variable = { t = surrender_progress }
            divide_temp_variable = { t = 10 }
            round_temp_variable = t
            factor = t
        }

        # Boost chance if the enemy is losing
        modifier = {
            any_country = {
                has_war_with = ROOT
                set_temp_variable = { t = surrender_progress }
                divide_temp_variable = { t = 10 }
                round_temp_variable = t
                factor = t
            }
        }
    }
}

music = {
    song = "MM_erika"
    chance = {
        base = 0

        # Enable if we are Germany or at war
        modifier = {
            add = 1

            OR = {
                TAG = GER
                has_war = yes
            }
        }

        # Boost chance if we are Germany and at war or at war with them
        modifier = {
            factor = 3
            
            OR = {
                AND = {
                    TAG = GER
                    has_war = yes
                }

                has_war_with = GER
            }
        }
    }
}

music = {
    song = "MM_china"
    chance = {
        base = 0

        # Enable if we are PRC or at war
        modifier = {
            add = 1

            OR = {
                TAG = PRC
                has_war = yes
            }
        }

        # Boost chance if we are PRC and at war or at war with them
        modifier = {
            factor = 3
            
            OR = {
                AND = {
                    TAG = PRC
                    has_war = yes
                }

                has_war_with = PRC
            }
        }
    }
}

music = {
    song = "MM_soviets"
    chance = {
        base = 0

        # Enable if we are USSR or at war
        modifier = {
            add = 1

            OR = {
                TAG = SOV
                has_war = yes
            }
        }

        # Boost chance if we are USSR and at war or at war with them
        modifier = {
            factor = 3
            
            OR = {
                AND = {
                    TAG = SOV
                    has_war = yes
                }

                has_war_with = SOV
            }
        }
    }
}
