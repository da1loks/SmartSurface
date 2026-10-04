# Конфигурация и эксплуатация

Этот репозиторий пока содержит документацию и изображения. Исходники и зависимости сборки отсутствуют.

## Описанные точки конфигурации

- `ROBOSURFACE_ARDUINO`: порт контроллера.
- `ROBOSURFACE_LIDAR`: порт лидара.
- `ROBOSURFACE_CAMERA`: устройство камеры.
- `robot_config.yaml`: движение, видео, сценарии, нейросеть и авторизация.
- `ekf.yaml`: источники и параметры фильтра одометрии.
- `robosurface.launch.py`: состав запуска.
- `NUXT_DIST`: путь к собранной статике интерфейса, описанный в заметках веб-узла.

## Диагностика после запуска существующей сборки

```sh
ros2 node list
ros2 topic list
ros2 topic info /cmd_vel
ros2 topic hz /scan
ros2 topic hz /odom
ros2 run tf2_tools view_frames
```

