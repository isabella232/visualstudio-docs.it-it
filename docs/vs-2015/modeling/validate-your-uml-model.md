---
title: Convalidare il modello UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c13a5e8ed5ae7fe778908af87958d4ed25951c1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812504"
---
# <a name="validate-your-uml-model"></a>Eseguire la convalida di un modello UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alcuni dei modelli UML che è possibile creare in Visual Studio potrebbero essere considerati non validi nel progetto. Ad esempio, è possibile richiedere che un caso di utilizzo sia sempre collegato a un diagramma di sequenza contenente le linee di vita che rappresentano gli attori del caso di utilizzo. È possibile installare o definire *vincoli* che consentono al team di conformarsi a requisiti come questo. I vincoli possono essere applicati quando l'utente salva o apre un modello e possono essere richiamati dal comando di menu.  
  
 Non vengono forniti vincoli con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], in quanto dipendono dal modo in cui il team interpreta e usa i modelli UML. È tuttavia possibile definire vincoli personalizzati e installare vincoli definiti da altri utenti. Per informazioni su come definire vincoli e assemblarli per la distribuzione, vedere [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="invoking-validation"></a>Richiamo di convalida  
 Dopo aver installato un'estensione della convalida, è possibile applicare vincoli che fornisce nei casi seguenti. Alcuni vincoli sono impostati in modo da essere applicati solo ad alcuni di questi casi.  
  
- **Comando di convalida.** Per richiamare la convalida in qualsiasi momento, fare clic su **convalida modello UML** nel **architettura** menu.  
  
  > [!NOTE]
  >  Il comando verrà visualizzato solo se i vincoli di convalida sono installati.  
  
- **Al salvataggio di un modello.** È possibile applicare vincoli di convalida quando si salva il modello. Lo scopo di questi vincoli è garantire che non si salvi un modello non valido in base all'interpretazione del progetto.  
  
   Se sono presenti errori, verrà chiesto se si vuole salvare il modello. È possibile scegliere di correggere gli errori o di salvare comunque il modello.  
  
- **All'apertura di un modello.** Quando si apre un modello, possono essere applicati metodi di convalida per ripristinare i messaggi di errore presenti quando è stato salvato il modello. Gli errori possono essere introdotti anche da incoerenze tra le modifiche apportate dagli utenti che lavorano su parti diverse di un modello. Per altre informazioni, vedere [condividere modelli ed esportare diagrammi](../modeling/share-models-and-exporting-diagrams.md).  
  
  Gli errori di convalida vengono segnalati nella finestra degli errori [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  Per selezionare in un diagramma gli elementi che non sono corretti, fare doppio clic sull'errore. Questo metodo funziona solo se gli elementi non corretti sono visibili in un diagramma aperto.  
  
## <a name="installing-validation-constraints"></a>Installazione dei vincoli di convalida  
 I vincoli vengono assemblati all'interno di file di estensione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). In genere, un insieme di vincoli è parte di un'estensione che contiene anche altre definizioni quali comandi di menu, profili ed elementi della casella degli strumenti.  
  
#### <a name="to-install-a-visual-studio-extension"></a>Per installare un'estensione di Visual Studio  
  
1.  Fare doppio clic il **VSIX** file in Windows Explorer (o Esplora File).  
  
2.  Riavviare un'eventuale istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] già in esecuzione.  
  
## <a name="disabling-and-uninstalling-validation-constraints"></a>Disabilitazione e disinstallazione dei vincoli di convalida  
 Quando si vuole usare un modello a cui non si applicano i vincoli, è possibile disabilitare temporaneamente l'estensione che li contiene. Abilitando e disabilitando estensioni diverse è possibile usare diversi tipi di modello in momenti diversi.  
  
#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Per disabilitare o disinstallare un'estensione di Visual Studio  
  
1.  Nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Tools** menu, fare clic su **estensioni e aggiornamenti**.  
  
2.  Insieme all'estensione, fare clic su **disabilitare** disabilitare temporaneamente l'estensione. È possibile riattivarlo in un secondo momento tornando al **estensioni e aggiornamenti** finestra.  
  
     \- oppure -  
  
     Fare clic su **Disinstalla** per rimuovere l'estensione.  
  
3.  Riavviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)   
 [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)



