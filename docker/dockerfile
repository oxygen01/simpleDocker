FROM runmymind/docker-android-sdk:alpine-standalone

# We then set our enviroment-paths as needed
ENV PATH $PATH:$ANDROID_SDK_HOME/platform-tools
ENV PATH $PATH:$ANDROID_SDK_ROOT/platform-tools:$ANDROID_SDK_ROOT/tools/emulator:$ANDROID_SDK_ROOT/tools
ENV PATH $PATH:$ANDROID_SDK_HOME/tools/bin

# After that we update the index of available packages and install python (needed for "gcloud")
RUN apk update
RUN apk add python

# Here we download and install all needed platform-tools, sdks, repositories, etc
# If changing/adding/deleting device configurations, this should be adopted to speed up build times
# Run "sdkmanager --list" for the exact strings
RUN sdkmanager "platform-tools" "platforms;android-25" "platforms;android-24"
RUN sdkmanager "build-tools;25.0.3" "build-tools;25.0.2"
RUN sdkmanager "extras;android;m2repository"
RUN sdkmanager "extras;m2repository;com;android;support;constraint;constraint-layout;1.0.2"
RUN sdkmanager "extras;m2repository;com;android;support;constraint;constraint-layout-solver;1.0.2"
RUN sdkmanager "extras;google;m2repository"
RUN sdkmanager --licenses
