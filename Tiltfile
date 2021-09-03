docker_build('srt-app','.', dockerfile='Dockerfile.live-transmit')
docker_build('srt-app-staticweb','.', dockerfile='Dockerfile.staticweb')

k8s_yaml('app-transmit.yaml')
k8s_resource('srt-app-transmit', port_forwards=[
    port_forward(9000, 9000, name='srt-tm-udp'),
    port_forward(9001, 9001, name='srt-tm-srt')
])

k8s_yaml('app-static.yaml')
k8s_resource('srt-app-staticweb', port_forwards=[
    port_forward(5000, 80, name='srt-tm-http')
])