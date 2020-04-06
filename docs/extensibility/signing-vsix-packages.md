---
title: Firma di pacchetti VSIX Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700095"
---
# <a name="signing-vsix-packages"></a>Firma di pacchetti VSIX
Gli assembly di estensione non devono essere firmati prima di poter essere eseguiti in Visual Studio, ma è consigliabile eseguire questa operazione.

 Se si desidera proteggere l'estensione e assicurarsi che non sia stata manomessa, è possibile aggiungere una firma digitale a un pacchetto VSIX. Quando un codice SSIX viene firmato, il programma di installazione VSIX visualizzerà un messaggio che indica che è firmato, oltre a ulteriori informazioni sulla firma stessa. Se il contenuto del progetto VSIX è stato modificato e il progetto VSIX non è stato firmato nuovamente, il programma di installazione di VSIX mostrerà che la firma non è valida. L'installazione non viene interrotta, ma l'utente viene avvisato.

> [!IMPORTANT]
> A partire da Visual Studio 2015, i pacchetti VSIX firmati con una firma diversa da SHA256 verranno identificati con una firma non valida. L'installazione di VSIX non è bloccata, ma l'utente verrà avvisato.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Firma di un valore VSIX con VSIXSignToolSigning a VSIX with VSIXSignTool
 È disponibile uno strumento di firma della crittografia SHA256 da [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) in nuget.org [in VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Per utilizzare VSIXSignTool

1. Aggiungere il progetto VSIX a un progetto.

2. Fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni, selezionare **Aggiungi &#124; Gestisci pacchetti NuGet**.  Per altre informazioni su NuGet e sull'aggiunta di pacchetti NuGet, vedere la [documentazione](/NuGet) di NuGet e gli argomenti [dell'interfaccia utente](/NuGet/Tools/Package-Manager-UI) di Gestione pacchetti.

3. Cercare VSIXSignTool da VisualStudioExtensibility e installare il pacchetto NuGet.Search for VSIXSignTool from VisualStudioExtensibility and install the NuGet package.

4. È ora possibile eseguire VSIXSignTool dal percorso dei pacchetti locali del progetto. Consultare la Guida della riga di comando dello strumento per lo scenario di firma (VSIXSignTool.exe /?).

   Ad esempio, per firmare con un file di certificato protetto da password:

   VSIXSignTool.exe sign \</f certfile \<> \</p password> file VSIX>

## <a name="see-also"></a>Vedere anche
- [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
