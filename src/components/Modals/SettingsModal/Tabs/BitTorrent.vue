<template>
  <v-container>
        <v-card flat>
          <v-card-text :style="{ minHeight: phoneLayout ? '' : '75vh'}">
                <h3>Privacy</h3>
                <div class="settings_content ml-5 mr-5">
                    <v-checkbox
                        dense
                        :label="`Enable DHT (decentralized network) to find more peers`"
                        v-model="settings.dht"
                    />
                    <v-checkbox
                        dense
                        :label="`Enable Peer Exchange (PeX) to find more peers`"
                        v-model="settings.pex"
                    />
                    <v-checkbox
                        dense
                        :label="`Enable Local Peer Discovery to find more peers`"
                        v-model="settings.lsd"
                    />
                    <v-checkbox
                        dense
                        :label="`Enable anonymous mode`"
                        v-model="settings.anonymous_mode"
                    />
                </div>

                <v-checkbox
                    dense
                    :label="`Torrent Queueing`"
                    v-model="settings.queueing_enabled"
                />
                <div class="settings_content ml-5 mr-5">
                    <v-text-field
                        class="mb-2"
                        outlined
                        dense
                        hide-details
                        :label="`Maximum active downloads`"
                        :disabled="!settings.queueing_enabled"
                        v-model="settings.max_active_downloads"
                    />
                    <v-text-field
                        class="mb-2"
                        outlined
                        dense
                        hide-details
                        :label="`Maximum active uploads`"
                        :disabled="!settings.queueing_enabled"
                        v-model="settings.max_active_uploads"
                    />
                    <v-text-field
                        class="mb-2"
                        outlined
                        dense
                        hide-details
                        :label="`Maximum active torrents`"
                        :disabled="!settings.queueing_enabled"
                        v-model="settings.max_active_torrents"
                    />

                    <v-checkbox
                        dense
                        :label="`Do not count slow torrents in these limits`"
                        v-model="settings.dont_count_slow_torrents"
                    />

                    <div class="settings_content">
                        <v-text-field
                            class="mb-2"
                            outlined
                            dense
                            hide-details
                            :label="`Download rate threshold KiB/s`"
                            :disabled="!settings.dont_count_slow_torrents"
                            v-model="settings.slow_torrent_dl_rate_threshold"
                        />
                        <v-text-field
                            class="mb-2"
                            outlined
                            dense
                            hide-details
                            :label="`Upload rate threshold KiB/s`"
                            :disabled="!settings.dont_count_slow_torrents"
                            v-model="settings.slow_torrent_ul_rate_threshold"
                        />
                        <v-text-field
                            class="mb-2"
                            outlined
                            dense
                            hide-details
                            :label="`Torrent inactivity timer`"
                            :disabled="!settings.dont_count_slow_torrents"
                            v-model="settings.slow_torrent_inactive_timer"
                        />
                    </div>
                </div>

                <h3>Seeding Limits</h3>
                <div class="settings_content ml-5 mr-5">
                    <v-row dense>
                        <v-col cols="10">
                            <v-checkbox
                                dense
                                :label="`When ratio reaches`"
                                v-model="settings.max_ratio_enabled"
                            />
                        </v-col>
                        <v-col>
                            <v-text-field
                                class="mb-2"
                                outlined
                                dense
                                hide-details
                                :disabled="!settings.max_ratio_enabled"
                                v-model="settings.max_ratio"
                            />
                        </v-col>
                    </v-row>
                    <v-row dense>
                        <v-col cols="10">
                            <v-checkbox
                                dense
                                label="When seeding time reaches"
                                v-model="settings.max_seeding_time_enabled"
                            />
                        </v-col>
                        <v-col>
                            <v-text-field
                                class="mb-2"
                                outlined
                                dense
                                hide-details
                                :disabled="!settings.max_seeding_time_enabled"
                                v-model="settings.max_seeding_time"
                            />
                        </v-col>
                    </v-row>
                </div>
            </v-card-text>
        </v-card>
    </v-container>
</template>

<script>
import { SettingsTab, FullScreenModal } from '@/mixins'

export default {
    name: 'BitTorrent',
    mixins: [SettingsTab, FullScreenModal]
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/SettingsTab.scss';
</style>
