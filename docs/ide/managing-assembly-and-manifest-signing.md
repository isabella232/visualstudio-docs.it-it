---
title: Gestione delle firme di assembly e manifesti
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cf721e9880ce7f0b7c3191f73f16366637f0704
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748880"
---
# <a name="manage-assembly-and-manifest-signing"></a>Gestione delle firme di assembly e manifesti

La firma con nome sicuro offre un'identità univoca globale per un componente software. I nomi sicuri sono usati per garantire che l'assembly non possa essere sottoposto a spoofing da parte di altri utenti e per verificare che le dipendenze dei componenti e le istruzioni di configurazione siano mappate al componente e alla versione del componente corretti.

Un nome sicuro è costituito dall'identità dell'assembly, corrispondente al nome semplice in formato testo, al numero di versione e alle informazioni sulle impostazioni cultura, più un token di chiave pubblica e una firma digitale.

Per informazioni sulla firma degli assembly nei progetti Visual Basic e C#, vedere [Creare e usare gli assembly con nome sicuro](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Per informazioni sulla firma degli assembly C++ nei progetti, vedere [assembly con nome sicuroC++(/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> La firma con nome sicuro non offre protezione da attacchi di reverse engineering dell'assembly. Per la protezione da attacchi di reverse engineering, vedere [Dotfuscator Community](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Tipi di asset e firma

È possibile firmare gli assembly .NET e i manifesti dell'applicazione:

- File eseguibili ( *.exe*)

- Manifesti dell'applicazione ( *.exe.manifest*)

- Manifesti della distribuzione ( *.application*)

- Assembly di componenti condivisi ( *.dll*)

Firmare i seguenti tipi di asset:

1. Assembly, se si vuole distribuirli alla Global Assembly Cache (GAC).

2. Manifesti della distribuzione e dell'applicazione ClickOnce. Visual Studio abilita la firma per impostazione predefinita per queste applicazioni.

3. Assembly di interoperabilità primari, usati per l'interoperabilità COM. L'utilità TLBIMP attiva l'assegnazione di nomi sicuri quando crea un assembly di interoperabilità primario da una libreria di tipi COM.

In generale è consigliabile non firmare i file eseguibili. Un componente con nome sicuro non può fare riferimento a un componente privo di nome sicuro distribuito con l'applicazione. Visual Studio non firma gli eseguibili dell'applicazione, consente invece di firmare il manifesto dell'applicazione, che fa riferimento al file eseguibile con nome debole. Evitare di firmare i componenti privati dell'applicazione, perché la firma può rendere più difficile la gestione delle dipendenze.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Come firmare un assembly in Visual Studio

Per firmare un'applicazione o un componente, usare la scheda **Firma** della finestra delle proprietà del progetto (fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**). Selezionare la scheda **Firma**, quindi la casella di controllo **Firma assembly**.

Specificare un file di chiave. Se si sceglie di creare un nuovo file di chiave, i nuovi file di chiave vengono sempre creati in formato *.pfx*. Sono necessari un nome e una password per il nuovo file.

> [!WARNING]
> Proteggere sempre il file di chiave con una password per impedire ad altri di usarlo. È possibile proteggere le chiavi usando provider o archivi certificati.

È anche possibile fare riferimento a una chiave già creata. Per altre informazioni sulla creazione delle chiavi, vedere [Creare una coppia di chiavi pubblica/privata](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Se si ha accesso solo a una chiave pubblica, è possibile usare il ritardo della firma per rinviare l'assegnazione della chiave. Per abilitare il ritardo della firma selezionare la casella di controllo **Ritarda firma**. Un progetto con firma ritardata non viene eseguito e non è possibile eseguirne il debug. Tuttavia, è possibile ignorare la verifica durante lo sviluppo usando lo [strumento nome sicuro Sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) con l'opzione `-Vr`.

Per informazioni sulla firma dei manifesti, vedere [Procedura: Firmare manifesti dell'applicazione e di distribuzione](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Vedere anche

- [Assembly con nomi sicuri](/dotnet/framework/app-domains/strong-named-assemblies)
- [Assembly con nomi sicuri (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
