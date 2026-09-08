FROM ros:humble
SHELL ["/bin/bash", "-c"]
ENV PIP_BREAK_SYSTEM_PACKAGES=1


# dependencies
RUN rm -f /etc/apt/apt.conf.d/docker-clean; echo 'Binary::apt::APT::Keep-Downloaded-Packages "true";' > /etc/apt/apt.conf.d/keep-cache
RUN --mount=target=/var/lib/apt/lists,type=cache,sharing=private \
    --mount=target=/var/cache/apt,type=cache,sharing=private \
    apt-get update --fix-missing && \
    apt-get upgrade -y && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:kisak/kisak-mesa -y && \
    apt-get update

RUN --mount=target=/var/lib/apt/lists,type=cache,sharing=private \
    --mount=target=/var/cache/apt,type=cache,sharing=private \
    apt-get install -y git \
                       nano \
                       vim \
                       python3-pip \
                       libeigen3-dev \
                       tmux \
    ros-humble-rosbridge-suite \
    ros-humble-rqt-graph \
    ros-humble-rviz2 \
    ros-humble-grid-map-rviz-plugin \
    ros-humble-joy \
    ros-humble-nav2-msgs \
    ros-humble-nav2-rviz-plugins \
    ros-humble-slam-toolbox \
    x11-xserver-utils \
    mesa-utils \
    libgl1-mesa-dri \
    libglx-mesa0 \
    mesa-vulkan-drivers \
    && apt-get dist-upgrade -y

#COPY client_config.xml /client_config.xml
ENV FASTRTPS_DEFAULT_PROFILES_FILE=/f1tenth_view/client_config.xml

ENTRYPOINT ["bash", "-c", "source /opt/ros/humble/setup.bash && ros2 run rviz2 rviz2"]
