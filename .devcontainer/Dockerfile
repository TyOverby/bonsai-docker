FROM ocaml/opam:alpine-ocaml-4.12@sha256:97d4da55048befbda12adc18765b049a9eb53a878bcce58dbfecb06f363273e8

USER root
RUN sed -i 's-/home/opam:/sbin/nologin-/home/opam:/bin/bash-' /etc/passwd
RUN apk add git neovim
RUN mkdir -p ~/.cache/nvim

USER opam
RUN opam pin add sexplib0 https://github.com/janestreet/sexplib0.git#master
RUN opam pin add base https://github.com/janestreet/base.git#master
RUN opam pin add sexplib https://github.com/janestreet/sexplib.git#master
RUN opam pin add parsexp https://github.com/janestreet/parsexp.git
RUN opam pin add bigarray-compat https://github.com/mirage/bigarray-compat.git
RUN opam install dune merlin ocamlformat ocaml-lsp-server js_of_ocaml js_of_ocaml-ppx

RUN mkdir vendor

RUN echo '(lang dune 1.10)' > ~/dune-project

RUN git clone https://github.com/janestreet/bonsai.git ./vendor/bonsai\
&& git clone https://github.com/janestreet/incr_dom.git ./vendor/incr_dom\
&& git clone https://github.com/janestreet/incremental.git ./vendor/incremental\
&& git clone https://github.com/janestreet/core_kernel.git ./vendor/core_kernel\
&& git clone https://github.com/janestreet/ppx_jane.git ./vendor/ppx_jane\
&& git clone https://github.com/janestreet/ppx_stable.git ./vendor/ppx_stable\
&& git clone https://github.com/janestreet/base_quickcheck.git ./vendor/base_quickcheck\
&& git clone https://github.com/janestreet/ppx_expect.git ./vendor/ppx_expect\
&& git clone https://github.com/janestreet/ppx_variants_conv.git ./vendor/ppx_variants_conv\
&& git clone https://github.com/janestreet/ppx_typerep_conv.git ./vendor/ppx_typerep_conv\
&& git clone https://github.com/janestreet/ppx_string.git ./vendor/ppx_string\
&& git clone https://github.com/janestreet/ppx_sexp_value.git ./vendor/ppx_sexp_value\
&& git clone https://github.com/janestreet/ppx_sexp_message.git ./vendor/ppx_sexp_message\
&& git clone https://github.com/janestreet/ppx_pipebang.git ./vendor/ppx_pipebang\
&& git clone https://github.com/janestreet/ppx_optcomp.git ./vendor/ppx_optcomp\
&& git clone https://github.com/janestreet/ppx_optional.git ./vendor/ppx_optional\
&& git clone https://github.com/janestreet/ppx_module_timer.git ./vendor/ppx_module_timer\
&& git clone https://github.com/janestreet/ppx_let.git ./vendor/ppx_let\
&& git clone https://github.com/janestreet/ppx_pattern_bind.git ./vendor/ppx_pattern_bind\
&& git clone https://github.com/janestreet/ppx_inline_test.git ./vendor/ppx_inline_test\
&& git clone https://github.com/janestreet/ppx_here.git ./vendor/ppx_here\
&& git clone https://github.com/janestreet/ppx_fixed_literal.git ./vendor/ppx_fixed_literal\
&& git clone https://github.com/janestreet/ppx_fields_conv.git ./vendor/ppx_fields_conv\
&& git clone https://github.com/janestreet/ppx_disable_unused_warnings.git ./vendor/ppx_disable_unused_warnings\
&& git clone https://github.com/janestreet/ppx_custom_printf.git ./vendor/ppx_custom_printf\
&& git clone https://github.com/janestreet/ppx_bin_prot.git ./vendor/ppx_bin_prot\
&& git clone https://github.com/janestreet/ppx_bench.git ./vendor/ppx_bench\
&& git clone https://github.com/janestreet/ppx_assert.git ./vendor/ppx_assert\
&& git clone https://github.com/janestreet/ppx_base.git ./vendor/ppx_base\
&& git clone https://github.com/janestreet/ppx_hash.git ./vendor/ppx_hash\
&& git clone https://github.com/janestreet/ppx_enumerate.git ./vendor/ppx_enumerate\
&& git clone https://github.com/janestreet/ppx_compare.git ./vendor/ppx_compare\
&& git clone https://github.com/janestreet/ppx_sexp_conv.git ./vendor/ppx_sexp_conv\
&& git clone https://github.com/janestreet/ppx_cold.git ./vendor/ppx_cold\
&& git clone https://github.com/janestreet/bin_prot.git ./vendor/bin_prot\
&& git clone https://github.com/janestreet/fieldslib.git ./vendor/fieldslib\
&& git clone https://github.com/janestreet/variantslib.git ./vendor/variantslib\
&& git clone https://github.com/janestreet/typerep.git ./vendor/typerep\
&& git clone https://github.com/janestreet/virtual_dom.git ./vendor/virtual_dom\
&& git clone https://github.com/janestreet/async_kernel.git ./vendor/async_kernel\
&& git clone https://github.com/janestreet/async_js.git ./vendor/async_js\
&& git clone https://github.com/janestreet/time_now.git ./vendor/time_now\
&& git clone https://github.com/janestreet/splittable_random.git ./vendor/splittable_random\
#&& git clone https://github.com/janestreet/sexplib.git ./vendor/sexplib\
&& git clone https://github.com/janestreet/jane-street-headers.git ./vendor/jane-street-headers\
&& git clone https://github.com/janestreet/base_bigstring.git ./vendor/base_bigstring\
&& git clone https://github.com/janestreet/int_repr.git ./vendor/int_repr\
#&& git clone https://github.com/janestreet/parsexp.git ./vendor/parsexp\
&& git clone https://github.com/janestreet/incr_select.git ./vendor/incr_select\
&& git clone https://github.com/janestreet/incr_map.git ./vendor/incr_map\
&& git clone https://github.com/janestreet/abstract_algebra.git ./vendor/abstract_algebra\
&& git clone https://github.com/LexiFi/gen_js_api.git ./vendor/gen_js_api\
&& git clone https://github.com/mirage/ocaml-uri.git ./vendor/ocaml-uri\
&& git clone https://github.com/janestreet/async_rpc_kernel.git ./vendor/async_rpc_kernel\
&& git clone https://github.com/janestreet/protocol_version_header.git ./vendor/protocol_version_header\
&& git clone https://github.com/inhabitedtype/angstrom.git ./vendor/angstrom\
&& git clone https://github.com/rgrinberg/stringext.git ./vendor/stringext\
&& git clone https://github.com/inhabitedtype/bigstringaf.git ./vendor/bigstringaf\
#&& git clone https://github.com/mirage/bigarray-compat.git ./vendor/bigarray-compat\
&& git clone https://github.com/janestreet/stdio.git ./vendor/stdio\
&& git clone https://github.com/janestreet/jst-config.git ./vendor/jst-config


RUN cd ~/vendor/bonsai && git checkout 761d04847d5f947318b64c0a46dffa17ad413536 && rm dune-project && mv bonsai.opam ~/\
&& cd ~/vendor/incr_dom && git checkout 56c04e44d6a8f1cc9b2b841495ec448de4bf61a1 && rm dune-project && mv incr_dom.opam ~/\
&& cd ~/vendor/incremental && git checkout a6a0161a9fe2295637260218eec0121ec3b83003 && rm dune-project && mv incremental.opam ~/\
&& cd ~/vendor/core_kernel && git checkout 18b2a732657ecac73e075e81e1edd0ef797fcc7d && rm dune-project && mv core_kernel.opam ~/\
&& cd ~/vendor/ppx_jane && git checkout a302242d4eedfa37233c31714316b2bfdec48979 && rm dune-project && mv ppx_jane.opam ~/\
&& cd ~/vendor/ppx_stable && git checkout 441eb6eccaf384d760cb2a8e5eb9fb4073deb591 && rm dune-project && mv ppx_stable.opam ~/\
&& cd ~/vendor/base_quickcheck && git checkout 19b40615b2aeb16e59e6023a6f2efbf01dbba8bd && rm dune-project && mv base_quickcheck.opam ~/\
&& cd ~/vendor/ppx_expect && git checkout 5d761232b0546e25a347313ab6bb211e42310f86 && rm dune-project && mv ppx_expect.opam ~/\
&& cd ~/vendor/ppx_variants_conv && git checkout 3b93fb3484588096127f46d7a7ec6651597f245a && rm dune-project && mv ppx_variants_conv.opam ~/\
&& cd ~/vendor/ppx_typerep_conv && git checkout 23c91aaa66916fe36b7c26e9a7a9b977ba17fc4a && rm dune-project && mv ppx_typerep_conv.opam ~/\
&& cd ~/vendor/ppx_string && git checkout master && rm dune-project && mv ppx_string.opam ~/\
&& cd ~/vendor/ppx_sexp_value && git checkout master && rm dune-project && mv ppx_sexp_value.opam ~/\
&& cd ~/vendor/ppx_sexp_message && git checkout master && rm dune-project && mv ppx_sexp_message.opam ~/\
&& cd ~/vendor/ppx_pipebang && git checkout master && rm dune-project && mv ppx_pipebang.opam ~/\
&& cd ~/vendor/ppx_optcomp && git checkout master && rm dune-project && mv ppx_optcomp.opam ~/\
&& cd ~/vendor/ppx_optional && git checkout master && rm dune-project && mv ppx_optional.opam ~/\
&& cd ~/vendor/ppx_module_timer && git checkout master && rm dune-project && mv ppx_module_timer.opam ~/\
&& cd ~/vendor/ppx_let && git checkout master && rm dune-project && mv ppx_let.opam ~/\
&& cd ~/vendor/ppx_pattern_bind && git checkout master && rm dune-project && mv ppx_pattern_bind.opam ~/\
&& cd ~/vendor/ppx_inline_test && git checkout master && rm dune-project && mv ppx_inline_test.opam ~/\
&& cd ~/vendor/ppx_here && git checkout master && rm dune-project && mv ppx_here.opam ~/\
&& cd ~/vendor/ppx_fixed_literal && git checkout master && rm dune-project && mv ppx_fixed_literal.opam ~/\
&& cd ~/vendor/ppx_fields_conv && git checkout master && rm dune-project && mv ppx_fields_conv.opam ~/\
&& cd ~/vendor/ppx_disable_unused_warnings && git checkout master && rm dune-project && mv ppx_disable_unused_warnings.opam ~/\
&& cd ~/vendor/ppx_custom_printf && git checkout master && rm dune-project && mv ppx_custom_printf.opam ~/\
&& cd ~/vendor/ppx_bin_prot && git checkout master && rm dune-project && mv ppx_bin_prot.opam ~/\
&& cd ~/vendor/ppx_bench && git checkout master && rm dune-project && mv ppx_bench.opam ~/\
&& cd ~/vendor/ppx_assert && git checkout master && rm dune-project && mv ppx_assert.opam ~/\
&& cd ~/vendor/ppx_base && git checkout master && rm dune-project && mv ppx_base.opam ~/\
&& cd ~/vendor/ppx_hash && git checkout master && rm dune-project && mv ppx_hash.opam ~/\
&& cd ~/vendor/ppx_enumerate && git checkout master && rm dune-project && mv ppx_enumerate.opam ~/\
&& cd ~/vendor/ppx_compare && git checkout master && rm dune-project && mv ppx_compare.opam ~/\
&& cd ~/vendor/ppx_sexp_conv && git checkout master && rm dune-project && mv ppx_sexp_conv.opam ~/\
&& cd ~/vendor/ppx_cold && git checkout master && rm dune-project && mv ppx_cold.opam ~/\
&& cd ~/vendor/bin_prot && git checkout master && rm dune-project && mv bin_prot.opam ~/\
&& cd ~/vendor/fieldslib && git checkout master && rm dune-project && mv fieldslib.opam ~/\
&& cd ~/vendor/variantslib && git checkout master && rm dune-project && mv variantslib.opam ~/\
&& cd ~/vendor/typerep && git checkout master && rm dune-project && mv typerep.opam ~/\
&& cd ~/vendor/virtual_dom && git checkout master && rm dune-project && mv virtual_dom.opam ~/\
&& cd ~/vendor/async_kernel && git checkout master && rm dune-project && mv async_kernel.opam ~/\
&& cd ~/vendor/async_js && git checkout master && rm dune-project && mv async_js.opam ~/\
&& cd ~/vendor/time_now && git checkout master && rm dune-project && mv time_now.opam ~/\
&& cd ~/vendor/splittable_random && git checkout master && rm dune-project && mv splittable_random.opam ~/\
#&& cd ~/vendor/sexplib && git checkout master && rm dune-project && mv sexplib.opam ~/\
&& cd ~/vendor/jane-street-headers && git checkout master && rm dune-project && mv jane-street-headers.opam ~/\
&& cd ~/vendor/base_bigstring && git checkout master && rm dune-project && mv base_bigstring.opam ~/\
&& cd ~/vendor/int_repr && git checkout master && rm dune-project && mv int_repr.opam ~/\
#&& cd ~/vendor/parsexp && git checkout master && rm dune-project && mv parsexp.opam ~/\
&& cd ~/vendor/incr_select && git checkout master && rm dune-project && mv incr_select.opam ~/\
&& cd ~/vendor/incr_map && git checkout master && rm dune-project && mv incr_map.opam ~/\
&& cd ~/vendor/abstract_algebra && git checkout master && rm dune-project && mv abstract_algebra.opam ~/\
&& cd ~/vendor/gen_js_api && git checkout master && rm dune-project && mv gen_js_api.opam ~/\
&& cd ~/vendor/ocaml-uri && git checkout master && rm dune-project && mv uri.opam ~/ && mv uri-sexp.opam ~/ && mv uri-re.opam ~/\
&& cd ~/vendor/async_rpc_kernel && git checkout master && rm dune-project && mv async_rpc_kernel.opam ~/\
&& cd ~/vendor/protocol_version_header && git checkout master && rm dune-project && mv protocol_version_header.opam ~/\
&& cd ~/vendor/angstrom && git checkout master && rm dune-project && mv angstrom.opam ~/ && mv angstrom-async.opam ~/ && mv angstrom-unix.opam ~/\
&& cd ~/vendor/stringext && git checkout master && rm dune-project && mv stringext.opam ~/\
&& cd ~/vendor/bigstringaf && git checkout master && rm dune-project && mv bigstringaf.opam ~/ \
#&& cd ~/vendor/bigarray-compat && git checkout master && rm dune-project && mv bigarray-compat.opam ~/\
&& cd ~/vendor/stdio && git checkout master && rm dune-project && mv stdio.opam ~/\
&& cd ~/vendor/jst-config && git checkout master && rm dune-project && mv jst-config.opam ~/


## PATCHES 

# Core is missing some fields and constructors
COPY ./core_diff.diff /home/opam
RUN cd ~/vendor/core_kernel && git apply ~/core_diff.diff

# Annotate packages for ppx binaries
run sed -i 's/install/install (package ppx_jane)/g' vendor/ppx_jane/bin/dune\
&& sed -i 's/install/install (package ppx_base)/g' vendor/ppx_base/bin/dune\
&& sed -i 's/install/install (package jst-config)/g' vendor/jst-config/src/dune

# Bigstringaf patches
RUN rm -rf vendor/bigstringaf/lib/freestanding
RUN sed -i 's/(foreign_stubs//g' vendor/bigstringaf/lib/dune\
&& sed -i 's/(language c)//g' vendor/bigstringaf/lib/dune\
&& sed -i 's/(names     bigstringaf_stubs)/(c_names bigstringaf_stubs)/g' vendor/bigstringaf/lib/dune\
&& sed -i 's/(flags.*$//g' vendor/bigstringaf/lib/dune

# Gen_js_api patches 
RUN rm vendor/gen_js_api/dune
RUN rm -rf vendor/gen_js_api/node-test  vendor/gen_js_api/ppx-test
RUN sed -i 's/ojs/gen_js_api/g' vendor/gen_js_api/lib/dune \
&& sed -i 's/gen_js_api_runtime.js/ojs_runtime.js/g' vendor/gen_js_api/lib/dune \
&& sed -i 's/ojs/gen_js_api/g' vendor/gen_js_api/ppx-driver/dune \
&& sed -i 's/ojs/gen_js_api/g' vendor/gen_js_api/ppx-lib/dune \
&& sed -i 's/(foreign_stubs//g' vendor/gen_js_api/lib/dune \
&& sed -i 's/(language c)//g' vendor/gen_js_api/lib/dune \
&& sed -i 's/(names gen_js_api_runtime_stubs))/(c_names ojs_runtime_stubs)/g' vendor/gen_js_api/lib/dune

# Angstrom patches
RUN rm -rf vendor/angstrom/lwt

## CLIENT
RUN echo '(env (dev (flags (:standard -w -16))))' > ~/dune
RUN opam install ppxlib
RUN bash -c "source ~/.profile && cd vendor/bonsai/examples/hello_world && dune build main.bc.js"




RUN git clone https://github.com/janestreet/core.git ./vendor/core\
&& git clone https://github.com/mirage/ocaml-cohttp.git ./vendor/cohttp\
&& git clone https://github.com/mirage/ocaml-ipaddr.git ./vendor/ipaddr\
&& git clone https://github.com/mirage/ocaml-conduit.git ./vendor/conduit\
&& git clone https://github.com/mirage/ocaml-magic-mime.git ./vendor/magic-mime\
&& git clone https://github.com/janestreet/async_rpc_websocket.git ./vendor/async_rpc_websocket\
&& git clone https://github.com/janestreet/cohttp_async_websocket.git ./vendor/cohttp_async_websocket\
&& git clone https://github.com/janestreet/async.git ./vendor/async\
&& git clone https://github.com/janestreet/ocaml_intrinsics.git ./vendor/ocaml_intrinsics\
&& git clone https://github.com/janestreet/timezone.git ./vendor/timezone\
&& git clone https://github.com/janestreet/spawn.git ./vendor/spawn\
&& git clone https://github.com/janestreet/async_extra.git ./vendor/async_extra\
&& git clone https://github.com/janestreet/async_ssl.git ./vendor/async_ssl\
&& git clone https://github.com/janestreet/async_unix.git ./vendor/async_unix\
&& git clone https://github.com/janestreet/async_websocket.git ./vendor/async_websocket\
&& git clone https://github.com/hannesm/domain-name.git ./vendor/domain-name\
&& git clone https://github.com/mirage/ocaml-base64.git ./vendor/base64\
&& git clone https://github.com/janestreet/ocaml-embed-file ./vendor/embed-file\
&& true

RUN cd ~/vendor/core && rm dune-project && mv core.opam ~/\
&& cd ~/vendor/cohttp && rm dune-project && mv cohttp.opam ~/ && mv cohttp-async.opam ~/ \ 
&& cd ~/vendor/conduit && rm dune-project && mv conduit.opam ~/ && mv conduit-async.opam ~/ \ 
&& cd ~/vendor/ipaddr && rm dune-project && mv ipaddr.opam ~/ && mv macaddr.opam ~/ && mv ipaddr-sexp.opam ~/ && mv macaddr-sexp.opam ~/ && mv ipaddr-cstruct.opam ~/ && mv macaddr-cstruct.opam ~/ \
&& cd ~/vendor/magic-mime && rm dune-project && mv magic-mime.opam ~/ \
&& cd ~/vendor/async_rpc_websocket && rm dune-project && mv async_rpc_websocket.opam ~/\
&& cd ~/vendor/cohttp_async_websocket && rm dune-project && mv cohttp_async_websocket.opam ~/\
&& cd ~/vendor/async && rm dune-project && mv async.opam ~/\
&& cd ~/vendor/timezone && rm dune-project && mv timezone.opam ~/\
&& cd ~/vendor/spawn && rm dune-project && mv spawn.opam ~/\
&& cd ~/vendor/async_extra && rm dune-project && mv async_extra.opam ~/\
&& cd ~/vendor/async_ssl && rm dune-project && mv async_ssl.opam ~/\
&& cd ~/vendor/async_websocket && rm dune-project && mv async_websocket.opam ~/\
&& cd ~/vendor/async_unix && rm dune-project && mv async_unix.opam ~/\
&& cd ~/vendor/ocaml_intrinsics && rm dune-project && mv ocaml_intrinsics.opam ~/\
&& cd ~/vendor/domain-name && rm dune-project && mv domain-name.opam ~/\
&& cd ~/vendor/base64 && rm dune-project && mv base64.opam ~/\
&& cd ~/vendor/embed-file && rm dune-project && mv ocaml-embed-file.opam ~/\
&& true


RUN rm vendor/core/dune
RUN rm -rf vendor/cohttp/cohttp/test\
&& rm -rf vendor/cohttp/cohttp-async/test\
&& rm -rf vendor/cohttp/cohttp-async/bin\
&& rm -rf vendor/cohttp/cohttp-lwt\
&& rm -rf vendor/cohttp/cohttp-lwt-jsoo\
&& rm -rf vendor/cohttp/cohttp-lwt-unix\
&& rm -rf vendor/cohttp/cohttp-mirage\
&& rm -rf vendor/cohttp/cohttp-top\
&& rm -rf vendor/cohttp/cohttp_lwt_jsoo_test\
&& rm -rf vendor/cohttp/examples\
&& rm -rf vendor/conduit/src/conduit-lwt*\
&& rm -rf vendor/conduit/src/conduit-mirage\
&& rm -rf vendor/conduit/tests\
&& rm -rf vendor/base64/test\
&& true

RUN sudo apk add libffi-dev gmp-dev zlib-dev openssl-dev
#RUN opam pin ctypes https://github.com/ocamllabs/ocaml-ctypes
#RUN opam pin ctypes-foreign https://github.com/ocamllabs/ocaml-ctypes
#RUN opam pin add async ~/vendor/async
#RUN opam pin add core ~/vendor/core
#RUN opam pin add core_kernel ~/vendor/core_kernel
#RUN opam pin add async_ssl https://github.com/janestreet/async_ssl.git
RUN opam install fmt logs ctypes ctypes-foreign cryptokit jsonm

RUN sed -i 's/(foreign_stubs//g' vendor/spawn/src/dune\
&& sed -i 's/(language c)//g' vendor/spawn/src/dune\
&& sed -i 's/(names spawn_stubs))/(c_names spawn_stubs)/g' vendor/spawn/src/dune\
&& rm -rf vendor/spawn/test \
&& true

RUN sed -i 's/ctypes.foreign.threaded/ctypes.foreign/g' vendor/async_ssl/bindings/dune
run sed -i 's/executables/executables (package ppx_jane)/g' vendor/embed-file/bin/dune
run echo 'module Cryptokit=Cryptokit' > vendor/async_websocket/src/crypto.ml
run echo 'module Foreign=Foreign' > vendor/async_ssl/bindings/ctypes_foreign_threaded_flat.ml

COPY ./core_thread_diff.diff /home/opam
RUN cd ~/vendor/core && git apply ~/core_thread_diff.diff
RUN rm vendor/async_ssl/bindings/ctypes_foreign_threaded_flat.ml

RUN bash -c "source ~/.profile && cd vendor/bonsai/examples/open_source/rpc_chat && dune build server/bin/main.exe"