/*
 * Copyright (c) Meta Platforms, Inc. and affiliates.
 *
 * This source code is licensed under the MIT license found in the
 * LICENSE file in the root directory of this source tree.
 */

#import <React/RCTUtils.h>

#import <React/RCTAlertController.h>

@interface RCTAlertController ()

@property (nonatomic, strong) UIWindow *alertWindow;

@end

@implementation RCTAlertController

- (UIWindow *)alertWindow
{
  if (_alertWindow == nil) {
    UIWindow *keyWindow = RCTSharedApplication().keyWindow;
    if (keyWindow) {
      _alertWindow = [[UIWindow alloc] initWithFrame:keyWindow.bounds];
      _alertWindow.rootViewController = [UIViewController new];
      _alertWindow.windowLevel = UIWindowLevelAlert + 1;
    } else {
      // keyWindow is nil, so we cannot create and initialize _alertWindow
      NSLog(@"Unable to create alert window: keyWindow is nil");
    }
  }

  return _alertWindow;
}

- (void)show:(BOOL)animated completion:(void (^)(void))completion
{
  UIUserInterfaceStyle style = self.overrideUserInterfaceStyle;
  if (style == UIUserInterfaceStyleUnspecified) {
    style = RCTSharedApplication().delegate.window.overrideUserInterfaceStyle
        ? RCTSharedApplication().delegate.window.overrideUserInterfaceStyle
        : UIUserInterfaceStyleUnspecified;
  }

  self.overrideUserInterfaceStyle = style;

  [self.alertWindow makeKeyAndVisible];
  [self.alertWindow.rootViewController presentViewController:self animated:animated completion:completion];
}

- (void)hide
{
  [_alertWindow setHidden:YES];

  _alertWindow.windowScene = nil;

  _alertWindow = nil;
}

<<<<<<< HEAD:packages/react-native/React/CoreModules/RCTAlertController.mm
- (UIWindow *)getUIWindowFromScene
{
  for (UIScene *scene in RCTSharedApplication().connectedScenes) {
    if (scene.activationState == UISceneActivationStateForegroundActive &&
        [scene isKindOfClass:[UIWindowScene class]]) {
      return [[UIWindow alloc] initWithWindowScene:(UIWindowScene *)scene];
    }
  }

  return nil;
}

=======
>>>>>>> parent of 0c53420a7af... Fix RCTAlertController not showing when using SceneDelegate on iOS 13.0+ (#35716):React/CoreModules/RCTAlertController.m
@end
