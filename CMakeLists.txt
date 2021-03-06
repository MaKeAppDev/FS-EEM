cmake_minimum_required(VERSION 2.8)

project(FS NONE)
include(UseLATEX)

add_custom_target(
    writegitid ALL
    COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/write-gitid.sh
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)

set(CHAPTERS
    chapters/grundlagen.tex
    chapters/permanentmagnete.tex
    chapters/gleichstrommaschine.tex
    chapters/wechselfeld.tex
    chapters/synchronmaschine.tex
    chapters/asynchronmaschine.tex
    chapters/universalmaschine.tex
    chapters/entwurf.tex
)

set(DRAWINGS
    drawings/grundlagen/maschinen-querschnitt.tex
    drawings/grundlagen/maschinen-querschnitt2.tex
    drawings/permanentmagnete/gsm_querschnitt.tex
    drawings/gleichstrommaschine/flussverlauf_phi.tex
    drawings/gleichstrommaschine/gsnsm_esb.tex
    drawings/gleichstrommaschine/gsrsm_esb.tex
    drawings/gleichstrommaschine/esb_pgsm.tex
    drawings/synchronmaschine/sm_esb.tex
    drawings/synchronmaschine/zeiger_syn.tex
    drawings/synchronmaschine/zeiger_syn_dq.tex
    drawings/synchronmaschine/zeiger_syn_generatorbetrieb.tex
    drawings/synchronmaschine/zeiger_syn_motorbetrieb.tex
    drawings/synchronmaschine/zeiger_syn_stromortskurve.tex
    drawings/asynchronmaschine/asm_esb.tex
    drawings/asynchronmaschine/zeiger_asyn.tex
    drawings/asynchronmaschine/zeiger_asyn_stromortskurve_i.tex
    drawings/asynchronmaschine/zeiger_asyn_stromortskurve_p.tex
    drawings/asynchronmaschine/zeiger_asyn_stromortskurve_s.tex
    drawings/universalmaschine/esb_uvm.tex
    drawings/universalmaschine/zeiger_uvm_stromortskurve.tex
    drawings/universalmaschine/zeiger_uvm.tex
    drawings/entwurf/bruchlochwicklung.tex
    drawings/entwurf/nutstern.tex
)

add_latex_document(
    formelsammlung.tex
    FORCE_PDF
    IMAGE_DIRS img
    INPUTS ${CHAPTERS} ${DRAWINGS}
    DEPENDS writegitid
)
