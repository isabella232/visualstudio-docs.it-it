---
title: 'Procedura: Profilare codice JavaScript nelle pagine Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 093054168a2314711476a5c4bc8a98ffdc6f732e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780760"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Procedura: Profilare codice JavaScript nelle pagine Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] possono raccogliere dati sulle prestazioni per il codice JavaScript eseguito in un'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], in una pagina Web arbitraria o in un'applicazione JavaScript usando il metodo di profilatura della strumentazione.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Internet Explorer 8 o versioni successive.  
  
> [!WARNING]
>  Per profilare JavaScript nelle applicazioni Windows Store, vedere uno degli argomenti seguenti:  
> 
> - [Temporizzazione funzione JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [temporizzazione funzione JavaScript in un dispositivo remoto](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   -   [Analizzare dati su Temporizzazione funzione JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   -  
  
 È possibile usare la procedura guidata di profilatura per creare una sessione di prestazioni. Specificare il metodo di strumentazione, quindi specificare l'opzione di profilatura JavaScript nella pagina Strumentazione della finestra di dialogo delle proprietà per la sessione di prestazioni.  
  
 Quando si specifica la profilatura JavaScript, questa viene applicata sia al codice JavaScript eseguito nel browser che al codice [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] eseguito nel server.  
  
-   Per un'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], la profilatura viene applicata sia al codice JavaScript eseguito nel browser che al codice [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] eseguito nel server.  
  
-   Per una pagina Web arbitraria, la profilatura viene applicata al codice JavaScript eseguito nel browser.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Per eseguire la profilatura di JavaScript in un progetto dell'applicazione Web ASP.NET  
  
1.  In [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] aprire il progetto Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2.  Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.  
  
3.  Nella prima pagina della procedura guidata, specificare il metodo di profilatura **Strumentazione** , quindi fare clic su **Avanti**.  
  
4.  Nella seconda pagina della procedura guidata, assicurarsi che il progetto corrente sia selezionato nell'elenco delle destinazioni, quindi fare clic su **Avanti**.  
  
5.  Nella terza pagina della procedura guidata, selezionare la casella di controllo **Profilo JavaScript** , quindi fare clic su **Avanti**.  
  
6.  Nella quarta pagina della procedura guidata, fare clic su **Fine** per avviare l'applicazione Web nel browser.  
  
7.  Verificare la funzionalità di cui eseguire la profilatura.  
  
8.  Per terminare la sessione di profilatura, chiudere il browser.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Per eseguire la profilatura del codice JavaScript in singole pagine Web o in applicazioni JavaScript  
  
1.  Aprire [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2.  Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.  
  
3.  Nella prima pagina della procedura guidata, specificare il metodo di profilatura **Strumentazione** , quindi fare clic su **Avanti**.  
  
4.  Nella seconda pagina della procedura guidata, fare clic su un'applicazione ASP.NET o JavaScript, quindi fare clic su **Avanti**.  
  
5.  Nella terza pagina della procedura guidata:  
  
    1.  Digitare l'URL della pagina nella casella **Specificare l'URL o il percorso che esegue l'applicazione Web** .  
  
    2.  Selezionare la casella di controllo **Profilo JavaScript** , quindi fare clic su **Avanti**.  
  
6.  Nella quarta pagina della procedura guidata, fare clic su **Fine** per avviare la pagina Web nel browser.  
  
7.  Verificare la funzionalità di cui eseguire la profilatura.  
  
8.  Per terminare la sessione di profilatura, chiudere il browser.
