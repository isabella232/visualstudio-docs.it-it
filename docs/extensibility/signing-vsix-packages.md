---
title: Firma dei pacchetti VSIX | Microsoft Docs
description: Informazioni sulla firma degli assembly di estensione. Il programma di installazione di VSIX visualizza un messaggio che indica che un vsix è firmato e le informazioni sulla firma stessa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d481c75754c7bc49369987d4bf6dc3aa33e96fdc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899160"
---
# <a name="signing-vsix-packages"></a>Firma di pacchetti VSIX
Gli assembly di estensione non devono essere firmati prima di poter essere eseguiti Visual Studio, ma è consigliabile farlo.

 Se si vuole proteggere l'estensione e assicurarsi che non sia stata manomesso, è possibile aggiungere una firma digitale a un pacchetto VSIX. Quando un file VSIX viene firmato, il programma di installazione VSIX visualizza un messaggio che indica che è firmato, oltre a ulteriori informazioni sulla firma stessa. Se il contenuto di VSIX è stato modificato e vsix non è stato firmato di nuovo, il programma di installazione VSIX mostrerà che la firma non è valida. L'installazione non viene arrestata, ma l'utente viene avvisato.

> [!IMPORTANT]
> A partire da Visual Studio 2015, i pacchetti VSIX firmati usando un valore diverso dalla crittografia SHA256 verranno identificati come con una firma non valida. L'installazione di VSIX non è bloccata, ma l'utente verrà avvisato.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Firma di un vsix con VSIXSignTool
 È disponibile uno strumento di firma della crittografia SHA256 in [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) nuget.org in [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Per usare VSIXSignTool

1. Aggiungere il vsix a un progetto.

2. Fare clic con il pulsante destro del mouse sul nodo Esplora soluzioni progetto e scegliere Aggiungi &#124; **Gestisci pacchetti NuGet**.  Per altre informazioni su NuGet e sull'aggiunta di pacchetti NuGet, vedere la documentazione di [NuGet](/NuGet) [e Gestione pacchetti'interfaccia](/NuGet/Tools/Package-Manager-UI) utente.

3. Cercare VSIXSignTool da VisualStudioExtensibility e installare il pacchetto NuGet.

4. È ora possibile eseguire VSIXSignTool dal percorso dei pacchetti locali del progetto. Consultare la Guida della riga di comando dello strumento per lo scenario di firma (VSIXSignTool.exe /?).

   Ad esempio, per firmare con un file di certificato protetto da password:

   VSIXSignTool.exe /f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Vedere anche
- [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
