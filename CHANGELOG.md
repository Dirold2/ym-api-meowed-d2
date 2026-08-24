# Changelog

## [1.5.0] — 2026-08-25

### Added

- `TrackApi.streamTrack()` streams a direct track download as `AsyncGenerator<Uint8Array>` without buffering the full file.

### Changed

- Updated `hyperttp` to `^0.5.2` and Bun/Undici transports to `^0.3.1`.
- Default API client now uses Hyperttp `baseURL`; relative API paths and query parameters are passed directly to the client.
- Bun transport bypasses response-cache reads and writes for streaming requests.
- Undici transport normalizes uncompressed Node `Readable` bodies to Web `ReadableStream<Uint8Array>`.

### Fixed

- Cancelling `streamTrack()` early now cancels and unlocks the response reader.
- Wrapped playlist URLs with numeric IDs now use the user playlist endpoint instead of the UUID playlist endpoint.
- Wrapped track URL IDs are converted to numeric IDs after URL extraction.

## [1.4.0] — 2026-06-23

### Added

#### New API domains
- **LabelApi** — `getLabel`, `getLabelAlbums`, `getLabelArtists`
- **CreditApi** — `getTrackCredits`, `getClipCredits`
- **DisclaimerApi** — `getTrackDisclaimer`, `getAlbumDisclaimer`, `getArtistDisclaimer`, `getClipDisclaimer`
- **MetatagApi** — `getMetatags`, `getMetatag`, `getMetatagAlbums`, `getMetatagArtists`, `getMetatagPlaylists`
- **ClipApi** — `getClips`, `getClipsWillLike`
- **PinApi** — `getPins`, `pinAlbum`, `unpinAlbum`, `pinArtist`, `unpinArtist`, `pinPlaylist`, `unpinPlaylist`, `pinWave`, `unpinWave`
- **PresaveApi** — `getPresaves`, `addPresave`, `removePresave`
- **MusicHistoryApi** — `getMusicHistory`, `getMusicHistoryItems`
- **DeviceAuthApi** — `requestDeviceCode`, `pollDeviceToken`, `deviceAuth`
- **ConcertApi** — `getArtistConcerts`, `getConcertInfo`, `getConcertSkeleton`, `getConcertsFeed`, `getConcertsLocations`, `getConcertsTabConfig`

#### Extended existing APIs

**UserApi:**
- `likeTracks`, `unlikeTracks`, `getLikedAlbums`, `likeAlbums`, `unlikeAlbums`
- `getLikedArtists`, `likeArtists`, `unlikeArtists`
- `getLikedPlaylists`, `likePlaylists`, `unlikePlaylists`
- `getLikedClips`, `likeClip`, `unlikeClip`
- `dislikeTracks`, `undislikeTracks`
- `getDislikedArtists`, `dislikeArtist`, `undislikeArtist`

**AlbumApi:**
- `getAlbumSimilarEntities`, `getAlbumTrailer`

**ArtistApi:**
- `getArtistBriefInfo`, `getArtistDirectAlbums`, `getArtistSimilar`, `getArtistLinks`
- `getArtistAlsoAlbums`, `getArtistDiscographyAlbums`, `getArtistSafeDirectAlbums`
- `getArtistTrackIds`, `getArtistAbout`, `getArtistClips`, `getArtistDonation`
- `getArtistInfo`, `getArtistSkeleton`, `getArtistTrailer`

**PlaylistApi:**
- `getPlaylistRecommendations` (alias `getPlaylistNew`), `getPlaylists`
- `setPlaylistVisibility`, `setPlaylistDescription`, `getPlaylistKinds`
- `getPlaylistTrailer`, `getPlaylistSimilarEntities`, `getUserSettings`
- `collectiveJoin`

**TrackApi:**
- `getTrackLyrics`, `getTrackTrailer`, `getTrackFullInfo`

### Types
- Added all TypeScript types for new methods (flat interfaces, no classes)
- Added exports for all new types in `src/Types/index.ts`
