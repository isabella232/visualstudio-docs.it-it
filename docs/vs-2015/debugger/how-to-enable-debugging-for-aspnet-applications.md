---
title: 'Procedura: abilitare il debug per le applicazioni ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726e964a0db2fae1b902f54a14e206dbc03a148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477004"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Come fare per: Attivare il debug per applicazioni ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per abilitare il debug, è necessario abilitarlo sia nella pagina **Proprietà progetto** sia nel file web.config dell'applicazione.  
  
> [!NOTE]  
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](/previous-versions/zbhkx167(v=vs.140)).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Per abilitare il debug di ASP.NET nelle proprietà del progetto (Visual Basic/C#)  
  
1. Fare clic con il pulsante destro del mouse sul nome del progetto Web in **Esplora soluzioni**, quindi scegliere **Proprietà**.  
  
2. Nella pagina delle proprietà del progetto fare clic sulla scheda **Web** .  
  
3. In **Debugger**selezionare la casella di controllo **ASP.NET** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Per abilitare il debug nel file web.config  
  
1. Aprire il file web.config usando qualsiasi editor di testo o parser XML standard.  
  
    > [!NOTE]  
    > Tuttavia, non è possibile accedere al file in remoto usando un Web browser. Per motivi di sicurezza, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] configura Microsoft IIS per prevenire l'accesso diretto del browser ai file Web.config. Se si prova ad accedere a un file di configurazione usando un browser, viene restituito l'errore di accesso HTTP 403 (accesso non consentito).  
  
2. Web.config è un file XML e di conseguenza contiene sezioni annidate contrassegnate da tag. Individuare l'elemento `configuration/system.web/compilation`. Se l'elemento di compilazione non esiste, è necessario crearlo.  
  
3. Se l'elemento `compilation` non contiene un attributo `debug` , aggiungere l'attributo all'elemento.  
  
4. Verificare che il valore dell'attributo `debug` sia impostato su `true`.  
  
Il file web.config dovrebbe essere analogo a quello dell'esempio seguente. Si noti che tra gli elementi di configurazione e system.web possono essere presenti sezioni.  
  
- Sezioni di elemento tra gli elementi di configurazione e system.web  
  
- Sezioni di elemento tra gli elementi system.web e di compilazione  
  
- L'elemento di compilazione può contenere altri attributi ed elementi  
  
## <a name="example"></a>Esempio  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Programmazione efficiente  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] rileva automaticamente qualsiasi modifica apportata ai file Web.config e applica le nuove impostazioni di configurazione. Non è necessario riavviare il computer o il server IIS server perché le modifiche abbiano effetto.  
  
Un sito Web può contenere più directory e sottodirectory virtuali, ognuna delle quali può includere file Web.config. Le applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ereditano le impostazioni dai file Web.config a livelli superiori nel percorso URL. I file di configurazione gerarchici permettono di modificare le impostazioni per diverse applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] contemporaneamente, ad esempio per tutte le applicazioni sottostanti nella gerarchia. Tuttavia, se `debug` è impostato in un file di livello inferiore nella gerarchia, eseguirà l'override del valore di livello superiore.  
  
Ad esempio, è possibile specificare `debug="true"` in `www.microsoft.com/aaa/Web.config` e qualsiasi applicazione nella cartella AAA o in qualsiasi sottocartella di aaa erediterà tale impostazione. Quindi, se l' [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applicazione si trova in `www.microsoft.com/aaa/bbb` , erediterà questa impostazione, così come tutte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] le applicazioni in `www.microsoft.com/aaa/ccc` , `www.microsoft.com/aaa/ddd` e così via. L'unica eccezione si verifica se una di queste applicazioni esegue l'ovveride dell'impostazione per mezzo del proprio file Web.config di livello inferiore.  
  
L'abilitazione della modalità di debug ha un notevole effetto sulle prestazioni dell'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Ricordare di disabilitare la modalità di debug prima di distribuire un'applicazione commerciale o di condurre misurazioni delle prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
[Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
