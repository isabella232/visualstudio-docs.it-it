---
title: Firma di pacchetti VSIX | Microsoft Docs
description: Informazioni sulla firma degli assembly di estensione. Il programma di installazione VSIX visualizza un messaggio che indica che un file VSIX è firmato e le informazioni sulla firma stessa.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c316f66a20f692ccdc20ed4b709efb0522e517d34b95f558be1e3ef30bbffe54
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413908"
---
# <a name="signing-vsix-packages"></a>Firma di pacchetti VSIX
Gli assembly di estensione non devono essere firmati prima di poter essere eseguiti in Visual Studio, ma è consigliabile farlo.

 Se si vuole proteggere l'estensione e assicurarsi che non sia stata manomesso, è possibile aggiungere una firma digitale a un pacchetto VSIX. Quando un file VSIX è firmato, il programma di installazione VSIX visualizza un messaggio che indica che è firmato e altre informazioni sulla firma stessa. Se il contenuto di VSIX è stato modificato e il file VSIX non è stato firmato di nuovo, il programma di installazione VSIX mostrerà che la firma non è valida. L'installazione non viene arrestata, ma l'utente viene avvisato.

> [!IMPORTANT]
> A partire Visual Studio 2015, i pacchetti VSIX firmati con un valore diverso dalla crittografia SHA256 verranno identificati come con una firma non valida. L'installazione di VSIX non viene bloccata, ma l'utente viene avvisato.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Firma di un file VSIX con VSIXSignTool
 È disponibile uno strumento di firma della crittografia SHA256 in [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) nuget.org in [VsixSignTool.](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)

#### <a name="to-use-the-vsixsigntool"></a>Per usare VSIXSignTool

1. Aggiungere il file VSIX a un progetto.

2. Fare clic con il pulsante destro del mouse sul nodo Esplora soluzioni progetto e **scegliere Aggiungi &#124; Gestisci NuGet pacchetti**.  Per altre informazioni sull'NuGet e sull'aggiunta NuGet pacchetti, vedere la [documentazione di NuGet](/NuGet) e gli [Gestione pacchetti'interfaccia](/NuGet/Tools/Package-Manager-UI) utente.

3. Cercare VSIXSignTool da VisualStudioExtensibility e installare NuGet pacchetto.

4. È ora possibile eseguire VSIXSignTool dal percorso dei pacchetti locali del progetto. Consultare la Guida della riga di comando dello strumento per lo scenario di firma (VSIXSignTool.exe /?).

   Ad esempio, per eseguire la firma con un file di certificato protetto da password:

   VSIXSignTool.exe /f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Vedi anche
- [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
