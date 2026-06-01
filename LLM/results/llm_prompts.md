## Prompt

We're building a 4-class classifier for music mood 
(Happy / Angry / Calm / Sad) on Spotify audio features. 
We CANNOT use valence or energy because we used them to derive the label.

Available features: danceability, loudness, tempo, acousticness, 
speechiness, instrumentalness, liveness, mode, key, 
time_signature, duration_ms, explicit.

Suggest 3 derived features that might help distinguish moods. 
For each, give a one-sentence intuition. 
Be concise — no preamble, no caveats.

## Raw Response

Here are three derived features:

1.  **Vocal Presence:** `speechiness * (1 - instrumentalness)`
    *   Intuition: This feature quantifies the prominence of vocal content, distinguishing tracks with strong vocal focus (e.g., aggressive speech for Angry, melodic singing for Happy) from purely instrumental ones.

2.  **Rhythmic Intensity:** `danceability * tempo`
    *   Intuition: This combines the groove and speed of a track, indicating its overall kinetic energy and potential for movement, which can differentiate high-energy moods (Happy, Angry) from low-energy ones (Calm, Sad).

3.  **Melancholy Chordality:** `acousticness * (1 - mode)`
    *   Intuition: This highlights acoustic tracks predominantly in a minor key (where `mode`=0), a combination often associated with feelings of sadness or introspective calmness.