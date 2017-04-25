XBUILD=/Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuild
PROJECT_ROOT=./TOCropViewController
PROJECT=$(PROJECT_ROOT)/TOCropViewController.xcodeproj
TARGET=TOCropViewController
IOSSDKVERSION=9.0

all: lib$(TARGET).a

lib$(TARGET)-i386.a:
	$(XBUILD) -project $(PROJECT) -target $(TARGET) -sdk iphonesimulator$(IOSSDKVERSION) -configuration Release clean build
	-mv $(PROJECT_ROOT)/build/Release-iphonesimulator/lib$(TARGET).a $@

lib$(TARGET)-armv7.a:
	$(XBUILD) -project $(PROJECT) -target $(TARGET) -sdk iphoneos$(IOSSDKVERSION) -arch armv7 -configuration Release clean build
	-mv $(PROJECT_ROOT)/build/Release-iphoneos/lib$(TARGET).a $@

lib$(TARGET)-arm64.a:
	$(XBUILD) -project $(PROJECT) -target $(TARGET) -sdk iphoneos$(IOSSDKVERSION) -arch arm64 -configuration Release clean build
	-mv $(PROJECT_ROOT)/build/Release-iphoneos/lib$(TARGET).a $@

lib$(TARGET).a: lib$(TARGET)-i386.a lib$(TARGET)-armv7.a lib$(TARGET)-arm64.a
	xcrun -sdk iphoneos$(IOSSDKVERSION) lipo -create -output $@ $^

clean:
	-rm -f *.a *.dll