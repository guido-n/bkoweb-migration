# bkoweb-migration

Lista dei files necessari per fare deployment della *functional slice* "avanzamento stato consegna"

## Front end

    web/WEB-INF/view/attivita/gestioneAttivita/gestioneRichieste/avanzamentoStatoConsegna.jsp
    web/WEB-INF/flow/easyticket/avanzamentoStatoConsegna/avanzamentoStatoConsegna.jsp
    web/WEB-INF/flow/attivita/gestioneAttivita/gestioneRichieste/avanzamento_stato_consegna/avanzamento_stato_consegna.jsp

    web/WEB-INF/view/include/common.jsp
    web/WEB-INF/view/include/collapsepanel.jsp

    web/WEB-INF/view/headerSempl.jsp
    web/WEB-INF/view/listErrors.jsp
    web/WEB-INF/view/header.jsp
    web/WEB-INF/view/footer.jsp

    web/WEB-INF/view/attivita/summaryAttivita.jsp
    web/WEB-INF/view/attivita/summaryRichiesta.jsp
    web/WEB-INF/view/attivita/gestioneAttivita/gestioneRichieste/gestioneRichiesteErrors.jsp
    web/WEB-INF/view/attivita/emailTemplate.jsp
    web/WEB-INF/view/attivita/gestioneAttivita/gestioneRichieste/avanzamentoStatoConsegna.jsp
    web/WEB-INF/view/attivita/carteggioList.jsp
    
    web/include/easyticket.js
    web/include/dhtml-suite-1.9.04/js/separateFiles/dhtmlSuite-common.js
    web/include/global.js
    web/include/collapse-panel/collapse-panel.js
    web/include/header.js

## Spring Web Flow
    
    web/WEB-INF/flow/easyticket/avanzamentoStatoConsegna/avanzamentoStatoConsegna-flow.xml
    web/WEB-INF/flow/attivita/gestioneAttivita/gestioneRichieste/avanzamento_stato_consegna/avanzamento_stato_consegna-flow.xml

## Spring beans

    allegatoAttivitaDAO
    anagraficaAccessoriLogisticaDAO
    anagraficaFornitoreLogisticaDAO
    anagraficaLoader
    anagraficaTransazioniDAO
    attivitaDAO
    attivitaManager
    attivitaUI
    breadcrumbAction
    commentoAttivitaDAO
    conformitaEmailDAO
    direzioneStoredEmailDAO
    documentServiceFactory
    emailAddressDAO
    emailDestinatarioDAO
    emailRicevutaService
    emailRicevuteAction
    emailRicevuteActionValidator
    emailTemplateDAO
    gestioneAllegatoAttivitaAction
    gestioneAllegatoAttivitaActionValidator
    gestioneRichiestaAscAction
    mailingListDAO
    mailSenderEasyTckService
    mailSenderService
    openTicketAction
    openTicketActionValidator
    protocolUtil
    richiestaManager
    richiestaUI
    richiestaValidator
    sessionAction
    statoAttivitaDAO
    statoConsegnaSapDAO
    storedEmailDAO
    storedEmailManager
    storedEmailUI
    templateDestinatarioDAO
    ticketBaseOrdineNumConsegnaAction
    ticketBaseOrdineNumConsegnaValidator
    ticketTrackingDAO
    tipoAttivitaDAO
    tipoDestinatarioDAO
    tipoOlDAO
    tipoProdottoDAO
    tipoRichiestaDAO
    tipoStoredEmailDAO
    userDAO
    userManager
    webContext
    webTransactionalManager

    declared in the following files:

    web/WEB-INF/spring/anagrafica-beans.xml
    web/WEB-INF/spring/attivita-beans.xml
    web/WEB-INF/spring/document-beans.xml
    web/WEB-INF/spring/email-beans.xml
    web/WEB-INF/spring/flusso-beans.xml
    web/WEB-INF/spring/global-beans.xml
    web/WEB-INF/spring/odvpda-beans.xml
    web/WEB-INF/spring/protocollo-beans.xml
    web/WEB-INF/spring/richiesta-beans.xml
    web/WEB-INF/spring/user-beans.xml
    web/WEB-INF/spring/workflow-beans.xml
    web/WEB-INF/spring/worklist-beans.xml