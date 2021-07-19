FROM ocaml/opam:alpine-ocaml-4.12@sha256:97d4da55048befbda12adc18765b049a9eb53a878bcce58dbfecb06f363273e8

USER root
RUN sed -i 's-/home/opam:/sbin/nologin-/home/opam:/bin/bash-' /etc/passwd
RUN apk add git neovim
RUN mkdir -p ~/.cache/nvim

USER opam
RUN opam pin add sexplib0 https://github.com/janestreet/sexplib0.git#master
RUN opam pin add base https://github.com/janestreet/base.git#master
RUN opam install dune merlin ocamlformat ocaml-lsp-server js_of_ocaml  js_of_ocaml-ppx

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
&& git clone https://github.com/janestreet/ppx_sexp_value.git ./vendor/ppx_sexp_value

RUN cd vendor/bonsai && git checkout 761d04847d5f947318b64c0a46dffa17ad413536 && rm dune-project && mv bonsai.opam ~/
RUN cd vendor/incr_dom && git checkout 56c04e44d6a8f1cc9b2b841495ec448de4bf61a1 && rm dune-project && mv incr_dom.opam ~/
RUN cd vendor/incremental && git checkout a6a0161a9fe2295637260218eec0121ec3b83003 && rm dune-project && mv incremental.opam ~/
RUN cd vendor/core_kernel && git checkout 18b2a732657ecac73e075e81e1edd0ef797fcc7d && rm dune-project && mv core_kernel.opam ~/
RUN cd vendor/ppx_jane && git checkout a302242d4eedfa37233c31714316b2bfdec48979 && rm dune-project && mv ppx_jane.opam ~/
run sed -i 's/install/install (package ppx_jane)/g' vendor/ppx_jane/bin/dune
RUN cd vendor/ppx_stable && git checkout 441eb6eccaf384d760cb2a8e5eb9fb4073deb591 && rm dune-project && mv ppx_stable.opam ~/
RUN cd vendor/base_quickcheck && git checkout 19b40615b2aeb16e59e6023a6f2efbf01dbba8bd && rm dune-project && mv base_quickcheck.opam ~/
RUN cd vendor/ppx_expect && git checkout 5d761232b0546e25a347313ab6bb211e42310f86 && rm dune-project && mv ppx_expect.opam ~/
RUN cd vendor/ppx_variants_conv && git checkout 3b93fb3484588096127f46d7a7ec6651597f245a && rm dune-project && mv ppx_variants_conv.opam ~/
RUN cd vendor/ppx_typerep_conv && git checkout 23c91aaa66916fe36b7c26e9a7a9b977ba17fc4a && rm dune-project && mv ppx_typerep_conv.opam ~/
RUN cd vendor/ppx_string && git checkout master && rm dune-project && mv ppx_string.opam ~/
RUN cd vendor/ppx_sexp_value && git checkout master && rm dune-project && mv ppx_sexp_value.opam ~/

RUN git clone https://github.com/janestreet/ppx_sexp_message.git ./vendor/ppx_sexp_message
RUN cd vendor/ppx_sexp_message && git checkout master && rm dune-project && mv ppx_sexp_message.opam ~/

RUN git clone https://github.com/janestreet/ppx_pipebang.git ./vendor/ppx_pipebang
RUN cd vendor/ppx_pipebang && git checkout master && rm dune-project && mv ppx_pipebang.opam ~/

RUN git clone https://github.com/janestreet/ppx_optcomp.git ./vendor/ppx_optcomp
RUN cd vendor/ppx_optcomp && git checkout master && rm dune-project && mv ppx_optcomp.opam ~/

RUN git clone https://github.com/janestreet/ppx_optional.git ./vendor/ppx_optional
RUN cd vendor/ppx_optional && git checkout master && rm dune-project && mv ppx_optional.opam ~/

RUN git clone https://github.com/janestreet/ppx_module_timer.git ./vendor/ppx_module_timer
RUN cd vendor/ppx_module_timer && git checkout master && rm dune-project && mv ppx_module_timer.opam ~/

RUN git clone https://github.com/janestreet/ppx_let.git ./vendor/ppx_let
RUN cd vendor/ppx_let && git checkout master && rm dune-project && mv ppx_let.opam ~/

RUN git clone https://github.com/janestreet/ppx_pattern_bind.git ./vendor/ppx_pattern_bind
RUN cd vendor/ppx_pattern_bind && git checkout master && rm dune-project && mv ppx_pattern_bind.opam ~/

RUN git clone https://github.com/janestreet/ppx_inline_test.git ./vendor/ppx_inline_test
RUN cd vendor/ppx_inline_test && git checkout master && rm dune-project && mv ppx_inline_test.opam ~/

RUN git clone https://github.com/janestreet/ppx_here.git ./vendor/ppx_here
RUN cd vendor/ppx_here && git checkout master && rm dune-project && mv ppx_here.opam ~/

RUN git clone https://github.com/janestreet/ppx_fixed_literal.git ./vendor/ppx_fixed_literal
RUN cd vendor/ppx_fixed_literal && git checkout master && rm dune-project && mv ppx_fixed_literal.opam ~/

RUN git clone https://github.com/janestreet/ppx_fields_conv.git ./vendor/ppx_fields_conv
RUN cd vendor/ppx_fields_conv && git checkout master && rm dune-project && mv ppx_fields_conv.opam ~/

RUN git clone https://github.com/janestreet/ppx_disable_unused_warnings.git ./vendor/ppx_disable_unused_warnings
RUN cd vendor/ppx_disable_unused_warnings && git checkout master && rm dune-project && mv ppx_disable_unused_warnings.opam ~/

RUN git clone https://github.com/janestreet/ppx_custom_printf.git ./vendor/ppx_custom_printf
RUN cd vendor/ppx_custom_printf && git checkout master && rm dune-project && mv ppx_custom_printf.opam ~/

RUN git clone https://github.com/janestreet/ppx_bin_prot.git ./vendor/ppx_bin_prot
RUN cd vendor/ppx_bin_prot && git checkout master && rm dune-project && mv ppx_bin_prot.opam ~/

RUN git clone https://github.com/janestreet/ppx_bench.git ./vendor/ppx_bench
RUN cd vendor/ppx_bench && git checkout master && rm dune-project && mv ppx_bench.opam ~/

RUN git clone https://github.com/janestreet/ppx_assert.git ./vendor/ppx_assert
RUN cd vendor/ppx_assert && git checkout master && rm dune-project && mv ppx_assert.opam ~/

RUN git clone https://github.com/janestreet/ppx_base.git ./vendor/ppx_base
RUN cd vendor/ppx_base && git checkout master && rm dune-project && mv ppx_base.opam ~/
run sed -i 's/install/install (package ppx_base)/g' vendor/ppx_base/bin/dune

RUN git clone https://github.com/janestreet/ppx_hash.git ./vendor/ppx_hash
RUN cd vendor/ppx_hash && git checkout master && rm dune-project && mv ppx_hash.opam ~/

RUN git clone https://github.com/janestreet/ppx_enumerate.git ./vendor/ppx_enumerate
RUN cd vendor/ppx_enumerate && git checkout master && rm dune-project && mv ppx_enumerate.opam ~/

RUN git clone https://github.com/janestreet/ppx_compare.git ./vendor/ppx_compare
RUN cd vendor/ppx_compare && git checkout master && rm dune-project && mv ppx_compare.opam ~/

RUN git clone https://github.com/janestreet/ppx_sexp_conv.git ./vendor/ppx_sexp_conv
RUN cd vendor/ppx_sexp_conv && git checkout master && rm dune-project && mv ppx_sexp_conv.opam ~/

RUN git clone https://github.com/janestreet/ppx_cold.git ./vendor/ppx_cold
RUN cd vendor/ppx_cold && git checkout master && rm dune-project && mv ppx_cold.opam ~/

RUN git clone https://github.com/janestreet/bin_prot.git ./vendor/bin_prot
RUN cd vendor/bin_prot && git checkout master && rm dune-project && mv bin_prot.opam ~/
# run sed -i 's/(c_names blit_stubs)/(foreign_stubs (language c) (names blit_stubs))/g' vendor/bin_prot/src/dune

RUN git clone https://github.com/janestreet/fieldslib.git ./vendor/fieldslib
RUN cd vendor/fieldslib && git checkout master && rm dune-project && mv fieldslib.opam ~/

RUN git clone https://github.com/janestreet/variantslib.git ./vendor/variantslib
RUN cd vendor/variantslib && git checkout master && rm dune-project && mv variantslib.opam ~/

RUN git clone https://github.com/janestreet/typerep.git ./vendor/typerep
RUN cd vendor/typerep && git checkout master && rm dune-project && mv typerep.opam ~/

RUN git clone https://github.com/janestreet/virtual_dom.git ./vendor/virtual_dom
RUN cd vendor/virtual_dom && git checkout master && rm dune-project && mv virtual_dom.opam ~/

RUN git clone https://github.com/janestreet/async_kernel.git ./vendor/async_kernel
RUN cd vendor/async_kernel && git checkout master && rm dune-project && mv async_kernel.opam ~/

RUN git clone https://github.com/janestreet/async_js.git ./vendor/async_js
RUN cd vendor/async_js && git checkout master && rm dune-project && mv async_js.opam ~/

RUN git clone https://github.com/janestreet/time_now.git ./vendor/time_now
RUN cd vendor/time_now && git checkout master && rm dune-project && mv time_now.opam ~/

RUN git clone https://github.com/janestreet/splittable_random.git ./vendor/splittable_random
RUN cd vendor/splittable_random && git checkout master && rm dune-project && mv splittable_random.opam ~/

RUN git clone https://github.com/janestreet/sexplib.git ./vendor/sexplib
RUN cd vendor/sexplib && git checkout master && rm dune-project && mv sexplib.opam ~/

RUN git clone https://github.com/janestreet/jane-street-headers.git ./vendor/jane-street-headers
RUN cd vendor/jane-street-headers && git checkout master && rm dune-project && mv jane-street-headers.opam ~/

RUN git clone https://github.com/janestreet/base_bigstring.git ./vendor/base_bigstring
RUN cd vendor/base_bigstring && git checkout master && rm dune-project && mv base_bigstring.opam ~/
#run sed -i 's/(c_names base_bigstring_stubs)/(foreign_stubs (language c) (names base_bigstring_stubs))/g' vendor/base_bigstring/src/dune

RUN git clone https://github.com/janestreet/int_repr.git ./vendor/int_repr
RUN cd vendor/int_repr && git checkout master && rm dune-project && mv int_repr.opam ~/

RUN git clone https://github.com/janestreet/parsexp.git ./vendor/parsexp
RUN cd vendor/parsexp && git checkout master && rm dune-project && mv parsexp.opam ~/

RUN git clone https://github.com/janestreet/incr_select.git ./vendor/incr_select
RUN cd vendor/incr_select && git checkout master && rm dune-project && mv incr_select.opam ~/

RUN git clone https://github.com/janestreet/incr_map.git ./vendor/incr_map
RUN cd vendor/incr_map && git checkout master && rm dune-project && mv incr_map.opam ~/

RUN git clone https://github.com/janestreet/abstract_algebra.git ./vendor/abstract_algebra
RUN cd vendor/abstract_algebra && git checkout master && rm dune-project && mv abstract_algebra.opam ~/

RUN git clone https://github.com/LexiFi/gen_js_api.git ./vendor/gen_js_api
RUN cd vendor/gen_js_api && git checkout master && rm dune-project && mv gen_js_api.opam ~/
RUN rm vendor/gen_js_api/dune
RUN rm -rf vendor/gen_js_api/node-test  vendor/gen_js_api/ppx-test
RUN sed -i 's/ojs/gen_js_api/g' vendor/gen_js_api/lib/dune \
&& sed -i 's/gen_js_api_runtime.js/ojs_runtime.js/g' vendor/gen_js_api/lib/dune \
&& sed -i 's/ojs/gen_js_api/g' vendor/gen_js_api/ppx-driver/dune \
&& sed -i 's/ojs/gen_js_api/g' vendor/gen_js_api/ppx-lib/dune \
&& sed -i 's/(foreign_stubs//g' vendor/gen_js_api/lib/dune \
&& sed -i 's/(language c)//g' vendor/gen_js_api/lib/dune \
&& sed -i 's/(names gen_js_api_runtime_stubs))/(c_names ojs_runtime_stubs)/g' vendor/gen_js_api/lib/dune
# RUN cat vendor/gen_js_api/lib/dune && false

RUN git clone https://github.com/mirage/ocaml-uri.git ./vendor/ocaml-uri
RUN cd vendor/ocaml-uri && git checkout master && rm dune-project && mv uri.opam ~/ && mv uri-sexp.opam ~/ && mv uri-re.opam ~/

RUN git clone https://github.com/janestreet/async_rpc_kernel.git ./vendor/async_rpc_kernel
RUN cd vendor/async_rpc_kernel && git checkout master && rm dune-project && mv async_rpc_kernel.opam ~/

RUN git clone https://github.com/janestreet/protocol_version_header.git ./vendor/protocol_version_header\
&& cd vendor/protocol_version_header && git checkout master && rm dune-project && mv protocol_version_header.opam ~/

RUN git clone https://github.com/inhabitedtype/angstrom.git ./vendor/angstrom\
&& cd vendor/angstrom && git checkout master && rm dune-project && mv angstrom.opam ~/ && mv angstrom-async.opam ~/ && mv angstrom-unix.opam ~/
RUN rm -rf vendor/angstrom/lwt

RUN git clone https://github.com/rgrinberg/stringext.git ./vendor/stringext\
&& cd vendor/stringext && git checkout master && rm dune-project && mv stringext.opam ~/

RUN git clone https://github.com/inhabitedtype/bigstringaf.git ./vendor/bigstringaf
RUN cd vendor/bigstringaf && git checkout master && rm dune-project && mv bigstringaf.opam ~/ 
RUN sed -i 's/(foreign_stubs//g' vendor/bigstringaf/lib/dune\
&& sed -i 's/(language c)//g' vendor/bigstringaf/lib/dune\
&& sed -i 's/(names     bigstringaf_stubs)/(c_names bigstringaf_stubs)/g' vendor/bigstringaf/lib/dune\
&& sed -i 's/(flags.*$//g' vendor/bigstringaf/lib/dune\
&& rm -rf vendor/bigstringaf/lib/freestanding
# RUN cat vendor/bigstringaf/lib/dune && false

RUN git clone https://github.com/mirage/bigarray-compat.git ./vendor/bigarray-compat\
&& cd vendor/bigarray-compat && git checkout master && rm dune-project && mv bigarray-compat.opam ~/

#RUN git clone https://github.com/janestreet/sexplib0.git ./vendor/sexplib0\
#&& cd vendor/sexplib0 && git checkout master && rm dune-project && mv sexplib0.opam ~/


RUN opam install ppxlib
#RUN git clone https://github.com/ocaml-ppx/ppxlib.git ./vendor/ppxlib\
#&& cd vendor/ppxlib && git checkout master && rm dune-project && mv ppxlib.opam ~/
#
#RUN sed -i 's/(cinaps//g' vendor/ppxlib/ast/dune\
#&& sed -i 's/(files \*.ml \*.mli)//g' vendor/ppxlib/ast/dune\
#&& sed -i 's/(libraries ast_cinaps_helpers))//g' vendor/ppxlib/ast/dune
#
#RUN sed -i 's/(cinaps//g' vendor/ppxlib/astlib/dune\
#&& sed -i 's/(files \*.ml \*.mli)//g' vendor/ppxlib/astlib/dune\
#&& sed -i 's/(libraries astlib_cinaps_helpers))//g' vendor/ppxlib/astlib/dune
#
#RUN sed -i 's/(re_export ppxlib_ast)//g' vendor/ppxlib/src/dune
#
#RUN sed -i 's/(cinaps//g' vendor/ppxlib/src/dune\
#&& sed -i 's/(files \*.ml \*.mli)//g' vendor/ppxlib/src/dune\
#&& sed -i 's/(libraries ppxlib_cinaps_helpers))//g' vendor/ppxlib/src/dune \
#&& rm -rf vendor/ppxlib/test

#RUN git clone https://github.com/janestreet/base.git ./vendor/base\
#&& cd vendor/base && git checkout master && rm dune-project && mv base.opam ~/

RUN git clone https://github.com/janestreet/stdio.git ./vendor/stdio\
&& cd vendor/stdio && git checkout master && rm dune-project && mv stdio.opam ~/

RUN git clone https://github.com/janestreet/jst-config.git ./vendor/jst-config\
&& cd vendor/jst-config && git checkout master && rm dune-project && mv jst-config.opam ~/\
&& sed -i 's/install/install (package jst-config)/g' src/dune

RUN echo '(env (dev (flags (:standard -w -16))))' > ~/dune

COPY ./core_diff.diff /home/opam
RUN cd vendor/core_kernel && git apply ~/core_diff.diff

RUN bash -c "source ~/.profile && cd vendor/bonsai/examples/hello_world && dune build main.bc.js"
#RUN bash -c "source ~/.profile; dune test"