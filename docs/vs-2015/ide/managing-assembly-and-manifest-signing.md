---
title: Gestione delle firme di assembly e manifesti | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab8ab81c83f98a7a35620db7cbb10a0f700d78e4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172744"
---
# <a name="managing-assembly-and-manifest-signing"></a>Gestione delle firme di assembly e manifesti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La firma con nome sicuro offre un'identità univoca globale per un componente software. I nomi sicuri sono usati per garantire che l'assembly non possa essere sottoposto a spoofing da parte di altri utenti e per verificare che le dipendenze dei componenti e le istruzioni di configurazione siano mappate al componente e alla versione del componente corretti.  
  
 Un nome sicuro è costituito dall'identità dell'assembly, corrispondente al nome semplice in formato testo, al numero di versione e alle informazioni sulle impostazioni cultura, più un token di chiave pubblica e una firma digitale.  
  
 Per informazioni sulla firma degli assembly nei progetti Visual Basic e C#, vedere [Creazione e utilizzo degli assembly con nome sicuro](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Per informazioni sulla firma degli assembly nei progetti Visual C++, vedere [Assembly con nome sicuro (firma degli assembly) (C++/CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).  
  
## <a name="asset-types-and-signing"></a>Tipi di asset e firma  
 È possibile firmare gli assembly .NET e i manifesti dell'applicazione, tra cui:  
  
-   file eseguibili (.exe)  
  
-   manifesti dell'applicazione (.exe.manifest)  
  
-   manifesti della distribuzione (.application)  
  
-   assembly di componenti condivisi (.dll)  
  
 È necessario firmare i seguenti tipi di asset:  
  
1.  assembly, se si vuole distribuirli alla Global Assembly Cache (GAC).  
  
2.  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesti di applicazione e distribuzione. Visual Studio abilita la firma per impostazione predefinita per queste applicazioni.  
  
3.  Assembly di interoperabilità primari, usati per l'interoperabilità COM. L'utilità TLBIMP attiva l'assegnazione di nomi sicuri quando crea un assembly di interoperabilità primario da una libreria di tipi COM.  
  
 In generale è consigliabile non firmare i file eseguibili. Un componente con nome sicuro non può fare riferimento a un componente senza nome sicuro distribuito con l'applicazione. Visual Studio non firma gli eseguibili dell'applicazione, consente invece di firmare il manifesto dell'applicazione, che fa riferimento al file eseguibile con nome debole. Non è in genere consigliabile firmare i componenti privati dell'applicazione, perché la firma può rendere più difficile la gestione delle dipendenze.  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Come firmare un assembly in Visual Studio  
 Per firmare un'applicazione o un componente, usare la scheda **Firma** della finestra delle proprietà del progetto (fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà** o digitare **proprietà del progetto** nella finestra **Avvio veloce** oppure premere ALT+INVIO nella finestra **Esplora soluzioni**. Selezionare la scheda **Firma**, quindi la casella di controllo **Firma assembly**.  
  
 Specificare un file di chiave. Se si sceglie di creare un nuovo file di chiave, tenere presente che i nuovi file di chiave vengono sempre creati in formato PFX. Sono necessari un nome e una password per il nuovo file.  
  
> [!WARNING]
>  Proteggere sempre il file di chiave con una password per impedire ad altri di usarlo. È possibile proteggere le chiavi usando provider o archivi certificati.  
  
 È anche possibile fare riferimento a una chiave già creata. Per altre informazioni sulla creazione delle chiavi, vedere [Procedura: Creare una coppia di chiavi pubblica/privata](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
 Se si ha accesso solo a una chiave pubblica, è possibile usare il ritardo della firma per rinviare l'assegnazione della chiave. Per abilitare il ritardo della firma selezionare la casella di controllo **Ritarda firma**. Un progetto con firma ritardata non verrà eseguito e non sarà possibile eseguirne il debug. Tuttavia, è possibile ignorare la verifica durante lo sviluppo usando [Sn.exe (strumento Nome sicuro)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) con l'opzione `-Vr`.  
  
 Per informazioni sulla firma dei manifesti, vedere [Procedura: Firmare manifesti dell'applicazione e di distribuzione](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Assembly con nomi sicuri](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Assembly con nome sicuro (firma degli assembly) (C++/CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)



