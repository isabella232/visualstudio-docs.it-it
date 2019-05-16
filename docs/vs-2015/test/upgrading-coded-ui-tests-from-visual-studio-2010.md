---
title: Aggiornamento dei test codificati dell'interfaccia utente
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4ab38f4fc7e0269c1073e71fae9975b240da33f2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695094"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Aggiornamento dei test codificati dell'interfaccia utente da Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I progetti di test contenenti test codificati dell'interfaccia utente creati in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 sono ripristinati senza avviso quando vengono aperti in Visual Studio 2012. Se i progetti di test vengono archiviati nel controllo del codice sorgente, i file di progetto vengono estratti per questo ripristino. Una volta ripristinati, questi progetti di test contenenti test codificati dell'interfaccia utente possono essere usati sia in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 che in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Requisiti**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio include più di un tipo di progetto di test. Un nuovo test codificato dell'interfaccia utente verrà creato in un tipo di progetto di test codificato dell'interfaccia utente. Per altre informazioni, vedere [Aggiornamento dei test da versioni precedenti di Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> I progetti di test di[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] contenenti test codificati dell'interfaccia utente devono essere ricompilati quando li si apre in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] o in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] affiancato a [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
> Quando un progetto di test creato in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] e contenente solo unit test viene aperto in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], non è possibile aggiungervi test codificati dell'interfaccia utente. Analogamente, non è possibile aggiungere un test codificato dell'interfaccia utente a un progetto di unit test creato in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problemi di compatibilità tra Visual Studio 2010 e Visual Studio 2012
 La seguente tabella elenca i problemi da tenere in considerazione quando si esegue la migrazione dei test codificati dell'interfaccia utente tra [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] e [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
> Esiste un problema noto relativo ai riferimenti nei progetti di test codificati dell'interfaccia utente non visualizzati in Esplora soluzioni. Per altre informazioni, vedere il file leggimi incluso nel supporto di installazione di [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

|Funzionalità interfaccia utente codificata|Problema|Soluzione|
|----------------------------|-----------|--------------|
|Il test dell'interfaccia utente di Silverlight non è supportato in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|**La compilazione avrà esito negativo**<br /><br /> Se si dispone di [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 e sono stati creati progetti di test codificato dell'interfaccia utente per applicazioni Silverlight, questi progetti non possono essere aperti in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|È consigliabile gestirli solo in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|Il test dell'interfaccia utente di Firefox non è supportato in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|**La compilazione avrà esito positivo, l'esecuzione del test avrà esito negativo**<br /><br /> Se si dispone di [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 e sono stati creati progetti di test codificato dell'interfaccia utente per applicazioni Web in Firefox, questi progetti non possono essere aperti in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|È consigliabile gestirli solo in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]sono state aggiunte nuove API di test del codice dell'interfaccia utente|**La compilazione avrà esito negativo**<br /><br /> Se si creano test codificati dell'interfaccia utente usando la nuova API di test dell'interfaccia utente in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], questi progetti non possono essere aperti in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|I progetti che usano la nuova API devono essere gestiti solo in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|
|In [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] sono stati aggiunti riferimenti all'interno di un'istruzione ‘Choose’ nel file csproj. In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], un file di destinazioni di feedback viene utilizzato per includere i riferimenti ad assembly di test codificato dell'interfaccia utente.|In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], un test codificato dell'interfaccia utente non può essere aggiunto a un progetto di test creato in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (o SP1) che non conteneva un test codificato dell'interfaccia utente.<br /><br /> Il processo di ripristino aggiunge il file di destinazioni e l'istruzione Choose. Se un test codificato dell'interfaccia utente non è nel progetto di test, il progetto viene contrassegnato come ripristinato e i riferimenti appropriati non verranno aggiunti quando si aggiungerà il test codificato dell'interfaccia utente in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Sarà necessario creare un nuovo progetto di test nella stessa soluzione usando [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] e aggiungervi il nuovo test codificato dell'interfaccia utente. In alternativa, è possibile aggiungere i test codificati dell'interfaccia utente nel progetto di test in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 e aprirlo in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

## <a name="UpgradingCodedUIFromVS2010_Update"></a> Aggiornamento di Visual Studio 2010 SP1
 Un aggiornamento a [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 con il supporto di compatibilità a Visual Studio 2012 e Windows 8 è disponibile per il download nell' [Area download Microsoft](http://www.microsoft.com/download/details.aspx?id=34677) nonché come aggiornamento di Visual Studio.

 Dopo avere applicato l'aggiornamento, le seguenti funzionalità dello strumento di test codificati dell'interfaccia utente [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 vengono aggiornate per Windows 8:

- È possibile eseguire un test codificato dell'interfaccia utente per i controlli WPF (Windows Presentation Foundation) basati su Microsoft .NET Framework 4.5 in un computer che esegue Windows 8.

- È possibile eseguire un test codificato dell'interfaccia utente per Internet Explorer 10 a 64 bit (x64) in un computer che esegue Windows 8.

  L'aggiornamento contiene anche le correzioni per i seguenti problemi:

- **Code coverage:** Impossibilità di aprire un file di code coverage (con estensione coverage) creato da Visual Studio 2012 in [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Artefatti di test abbandonati:** Il team dispone di un elemento di test assegnato a un utente non valido in Team Foundation Server (TFS) 2010. Ad esempio, un utente ha lasciato l'azienda, ma un test case è ancora assegnato a lui. Eseguire l'aggiornamento di TFS 2010 a TFS 2012. Utilizzare [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 per connettersi al server TFS aggiornato. Non è possibile assegnare l'elemento di test ad alcuni utenti TFS utilizzando [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Test di carico:** Quando si esegue un test di carico con un tipo di rete diverso dal profilo della rete locale (LAN) in un computer che esegue Windows 8, il driver dell'emulatore di rete causa l'arresto anomalo del sistema operativo. Per altre informazioni, vedere l' [articolo KB 2736182](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Vedere anche
 [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [aggiornamento dei test da versioni precedenti di Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md) [la generazione di un Test codificati dell'interfaccia utente Test da una registrazione delle azioni esistente](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
