buildDocker(
    rclone: [
        from: '/Anpassung Referenzen/',
        to: 'src/assets/referenzen/',
        // you can ignore the trailing space here. it isn't required and
        // is just there to make the lsp happy. it has no functional effect
        extraArgs: [
            '--include',
            '/{{referenz-\d+/[^/]+\.(json|jpg|png)}}'
        ]
    ],
    compressed_caching: false
)
