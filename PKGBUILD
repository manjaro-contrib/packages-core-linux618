# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

_basekernel=6.18
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=ec714e371f22f716a04e6ecb2a24988c92b26911
_rc=rc0
pkgbase=linux${_basever}
pkgver=6.18.0rc0
pkgrel=3
arch=('x86_64')
url="https://www.kernel.org/"
license=(GPL-2.0-only)
makedepends=(
  bc
  cpio
  gettext
  libelf
  pahole
  perl
  python
  rust
  rust-bindgen
  rust-src
  tar
  xz
)
options=(
  !debug
  !strip
)
source=(#"https://www.kernel.org/pub/linux/kernel/v6.x/linux-${_basekernel}.tar.xz"
        #https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}-${_rc}.tar.gz
        #https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}.tar.gz
        #https://git.kernel.org/torvalds/t/linux-${_basekernel}-${_rc}.tar.gz
        https://github.com/torvalds/linux/archive/${_commit}.tar.gz
        #https://www.kernel.org/pub/linux/kernel/v6.x/patch-${pkgver}.xz
        config
        # Upstream Patches
        0000-drm-amdgpu-fix-race-condition-in-amdgpu_vm_wait_idle-during-process-kill.patch::https://lore.kernel.org/all/20250807084655.1597669-1-Tong.Liu01@amd.com/raw
        # Turn off custom brightness-curve when nonsense is found in BIOS
        0001-drm-amd-Sanity-check-custom-brightness-curve-data-po.patch
        # https://www.phoronix.com/news/AMD-Color-Management-Patches
        0000-amd-display-move-AMD_PRIVATE_COLOR-to-Kconfig.patch
        # From Valve for Upstream (fixes suspend on deck target in inputplumber)
        0000-usb-vhci-hcd-Unconditionally-allow-system-suspend.patch
        # ARCH Patches
        0001-add-sysctl-to-disallow-unprivileged-CLONE_NEWUSER-by.patch
        0002-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        # Manjaro Patches
        # Realtek patch
        0999-patch_realtek.patch
        # ROG ALLY Patches (wip/ally-6.14-refactor)
        0002-hid-add-VID-PID-for-ASUS-ROG-RAIKIRI-PRO.patch
        0000-v12-0-8-platform-x86-Add-asus-armoury-driver.patch
        0014-asus-ally-hid-add-new-driver-for-ASUS-Ally-handhelds.patch
        0015-asus-ally-hid-Add-joystick-LED-ring-support.patch
        0016-asus-ally-hid-initial-Ally-X-gamepad-bringup.patch
        0017-asus-ally-hid-add-QAM-steam-action-attribute-to-disa.patch
        0018-asus-ally-hid-add-force-feedback-to-Ally-X-gamepad.patch
        0019-asus-ally-hid-handle-screenside-QAM-buttons.patch
        0020-asus-ally-hid-rename-input-devices.patch
        0021-asus-ally-hid-add-gamepad-config-structures.patch
        0022-asus-ally-hid-test-vibe.patch
        0023-asus-ally-hid-add-deadzone-and-outer-threshold-to-JS.patch
        0024-asus-ally-hid-test-trigger-dzot.patch
        0025-asus-ally-hid-test-js-anti-deadzone.patch
        0026-asus-ally-hid-test-joystick-response-curves.patch
        0027-asus-ally-hid-test-btn-turbo.patch
        0028-asus-ally-hid-test-gamepad-mode.patch
        0029-ally-tmp-remapping.patch
        0030-asus-wmi-fixup-screenpad-brightness.patch
        # OrangePi Neo patches
        0001-iio_imu_Add_driver_for_Bosch_BMI260_IMU.patch
        # Zotac Zone patches
        0001-zotac-zone-hid-initial-impl.patch
        0002-xpad-gate-the-zotac-zone-PID-behind-if-IS_REACHABLE-.patch
        0003-tmp-apply-zotac-screen-quirk.patch
        0005-zone-fix-6.15-rename-del_timer-to-timer_delete.patch
        # Steamdeck (OLED)
        0001-steam-deck.patch
        # Lenovo Legion Go S
        0000-HID-Add-Legion-Go-S-Driver.patch::https://patchwork.kernel.org/series/978420/mbox/
        # AMD patches
        # https://www.phoronix.com/news/AMD-ISP4-Linux-Driver-v3
        0000-v3-1-7-media-platform-amd-Introduce-amd-isp4-capture-driver.patch
)

if [[ ! -z "$_commit" ]]; then
  _srcdir="linux-${_commit}"
elif [[ ! -z "$_rc" ]]; then
  _srcdir="linux-${_basekernel}-${_rc}"
else
  _srcdir="linux-${_basekernel}"
fi

sha256sums=('65391e059d943d293cf8f306442fa32fff08b35d9b9ce21cad42c98ea45ed14b'
            '64593456bb9b35efe4d20872706f046f278e72416d6ce4ee4c7268c3320748a7'
            '37f3222fafbe67dec3740933be37867e0c378468f71e9a6d5d6a07c2a2a568fe'
            'cacb08b2f43a9fd09053bffaacc4b7bdf8381772f26e61825fb696ded100af57'
            '17314afeea1c80984eb8d7ff2c06adedd78655bf795a6a232992ee3082b773b6'
            '512032c6b93fce24254da6cace7bf101c8f7c824761a0f99deed4b7724ac6f3e'
            'e5e98d62b63704cecdf32dbe6a9bafea6e70b23fa8e01fe96ca220ac6036392e'
            'c21170eba77438abb8b8ab02aeccf16bfb2467a01303509945aa6b3a0fd16d31'
            '103688f3fceff664c919d94faab7a6948880710641110eaa71fe107ee06c37e9'
            'e5671d5f6fe27c072397efeedb876912d52e104488baa8cd149727ff0814e657'
            '224f09138c6c5b01b938f3b6bc80530d1048ec82455b837120c30074c70bc3fb'
            '1be445ba5698e135c32433c2bca3334c580d8d72dc3111d423dcc8d2da228e41'
            '5d73542ba4aa68d0b00b044a4a3eb2ca8fbfbb16790edbb22417cffeec4caade'
            'f91b213a05b679f14f2c61b14fbd2dda69950e17ded5d3b1e08eab09b8656f19'
            '1e55d30afbd5e1948685bdf08768b1f3961ec5713b8dfe869fdd494b039e5a08'
            '7da67f4e4628a1bd8adba3040e91c42b1c2ac620ffc76d2609dab0a026878976'
            '3f58f4bf292bca23fafa946fe6d86f2c5fbce84a609dc177f2081d69dab8fd1d'
            '6bb40862279ea8647ba62117b6a615853965e24789145690fa30abdb1e705f05'
            '36fb699a17ad59871366348a7cc031bf4fc42ebb7f9b15d22a5ede763f9518de'
            'b83b272409c3fac18e0e7d21dc0230652130ae1abc7386893ae2c4cbf7ace01a'
            'cf2c859f55a045d054c5381675327a1570e98228c4871c06e53d246f1ca5285c'
            'f0bea9dae7b29fb4980c0fa506be7219d022716cb51df70dcd0230156a808ecb'
            '763020ec985dea291e6009dfed274eae735c8c69872d816c2c83c065a1251329'
            '36eae257663af1df644f1a7819c03bc33c290a7bbcb319fb1e05668f198b5a81'
            'ca69d6815b1d23a2e31e5453dadccb22c03ae9e36d5cd29dd8d8389b1437dff4'
            '9bafa4955c27d3668d3827e3fbd9aad00195f581d3b5c9f37a4059420e504a1d'
            '8e6f050f3e176e7076d0f11375be55b07689d599c37ddb406c7494ea54232247'
            'e332e8137eec1f74e8cdfe27baad2a738620ef3498bca19be9c934044de0fa78'
            '14278fdc353e6ab5abc9c1a6b753221df12c9a0e6a8d9fec8baf81d7897a6a4b'
            'b67f25c13e946b51712b0e828ebbf8bea980d339bd6effab17869f6a62e428df'
            'c30d45e2ccde056b277246321040164f70db8adb8b8335a2fbdd4a2bf74b97cf'
            '138684588665b8f651dffb4e75c265a2b81f6bd7a606f75f8fc6814a4a63d3fd'
            '3d37e1f54290bad1b7a4c5c45046341dc4c1bfc2f8648b7754bf0bd9705b3a35'
            'f8cf8ad3e17857b51c3f7dd954eb5ac7ba44bfe0302a40e70b2c496573407edf'
            'adbb2ad0ea9a3e1591131af5fb4380aeeac27172be5c6faade459514e28c071a'
            '160a78e648189f9e09f3c64d665ef9b21a4b0b0b78ad429e8afb38635ec7b0fe')

export KBUILD_BUILD_HOST=manjaro
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

prepare() {
  cd $_srcdir

  echo "Setting version..."
  echo "-$pkgrel" > localversion.10-pkgrel

  # add upstream patch
  if [[ -z "$_rc" ]] && [[ -e "../patch-${pkgver}" ]]; then
    msg "add upstream patch"
    patch -p1 -i "../patch-${pkgver}"
  fi

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    src="${src%.zst}"
    [[ $src = *.patch ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  echo "Setting config..."
  cp ../config .config
  make olddefconfig
  diff -u ../config .config || :

  msg "set PATCHLEVEL to 18"
  sed -ri "s|^(PATCHLEVEL =).*|\1 18|" Makefile
  
  msg "set EXTRAVERSION to ${_rc}"
  sed -ri "s|^(EXTRAVERSION =).*|\1 -${_rc}|" Makefile

  make -s kernelrelease > version
  msg "Prepared $pkgbase version $(<version)"
}

build() {
  cd $_srcdir
  make ${MAKEFLAGS} bzImage modules
  make -C tools/bpf/bpftool vmlinux.h feature-clang-bpf-co-re=1
}

_package() {
  pkgdesc="The Linux $_basekernel kernel and modules"
  depends=(
    'coreutils'
    'initramfs'
    'kmod'
  )
  optdepends=(
    'linux-firmware: firmware images needed for some devices'
    'scx-scheds: to use sched-ext schedulers'
    'wireless-regdb: to set the correct wireless channels of your country'
  )
  provides=(
    "linux=${pkgver}"
    KSMBD-MODULE
    VIRTUALBOX-GUEST-MODULES
    WIREGUARD-MODULE
  )
  replaces=(
    virtualbox-guest-modules
    wireguard
  )

  cd $_srcdir
  local modulesdir="$pkgdir/usr/lib/modules/$(<version)"

  echo "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"
  echo "${_basekernel}-${CARCH}" | install -Dm644 /dev/stdin "$modulesdir/kernelbase"

  # add kernel version
  mkdir -p "${pkgdir}/boot"
  echo "$(<version) x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  echo "Installing modules..."
  ZSTD_CLEVEL=19 make INSTALL_MOD_PATH="$pkgdir/usr" INSTALL_MOD_STRIP=1 \
    DEPMOD=/doesnt/exist modules_install  # Suppress depmod

  # remove build link
  rm "$modulesdir"/build

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "$(<version)"
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the Linux $_basekernel kernel"
  depends=(pahole)

  cd $_srcdir
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux tools/bpf/bpftool/vmlinux.h
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts
  ln -srt "$builddir" "$builddir/scripts/gdb/vmlinux-gdb.py"

  # required when STACK_VALIDATION is enabled
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # required when DEBUG_INFO_BTF_MODULES is enabled
  install -Dt "$builddir/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/x86" -a arch/x86/include
  install -Dt "$builddir/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

  install -Dt "$builddir/drivers/md" -m644 drivers/md/*.h
  install -Dt "$builddir/net/mac80211" -m644 net/mac80211/*.h

  # https://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "$builddir/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

  echo "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  echo "Removing documentation..."
  rm -r "$builddir/Documentation"

  echo "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local file
  while read -rd '' file; do
    case "$(file -Sib "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip -v $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v $STRIP_SHARED "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v $STRIP_STATIC "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"
}

pkgname=(
  "$pkgbase"
  "$pkgbase-headers"
)
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
