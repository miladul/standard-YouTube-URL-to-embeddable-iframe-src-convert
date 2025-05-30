# standard-YouTube-URL-to-embeddable-iframe-src-convert
converts a standard YouTube URL into an embeddable iframe src link

#Add this to your helper file (e.g., app/Helpers/functions/helpers.php):

```
if (!function_exists('youtubeToIframeSrc')) {
    /**
     * Convert a YouTube URL to an iframe-compatible src link.
     *
     * @param string $url
     * @return string|null
     */
    function youtubeToIframeSrc(string $url): ?string
    {
        // Match common YouTube URL formats
        preg_match(
            '%(?:youtube(?:-nocookie)?\.com/(?:[^/]+/.+/|(?:v|embed)/|.*[?&]v=)|youtu\.be/)([^"&?/ ]{11})%i',
            $url,
            $matches
        );

        if (!empty($matches[1])) {
            return 'https://www.youtube.com/embed/' . $matches[1];
        }

        return null; // Invalid YouTube URL
    }
}

```

