modularPipeline([
    nextcloudRcloneStage(
        name: 'referenzen',
        url: 'nextcloud-url',
        username: 'nextcloud-username',
        password: 'nextcloud-password',
        from: '/Anpassung Referenzen/',
        to: 'src/assets/referenzen/',
        extraArgs: [
            '--include',
            '/{{referenz-\\d+/[^/]+\\.(json|jpg|png)}}'
        ]
    ),
    dockerStage(
        unstash: [
            'referenzen',
        ],
        compressed_caching: false,
    ),
])
