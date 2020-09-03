---
title: Firma di pacchetti VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4efaaa78ce593d8b97d1df454a9c30c2e62d9f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918729"
---
# <a name="signing-vsix-packages"></a>Firma di pacchetti VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli assembly di estensione non devono essere firmati prima di poter essere eseguiti in Visual Studio, ma è consigliabile farlo.  
  
 Se si vuole proteggere l'estensione e assicurarsi che non sia stata manomessa, è possibile aggiungere una firma digitale a un pacchetto VSIX. Quando un progetto VSIX è firmato, il programma di installazione VSIX Visualizza un messaggio che indica che è firmato, più altre informazioni sulla firma stessa. Se il contenuto di VSIX è stato modificato e il progetto VSIX non è ancora stato firmato, il programma di installazione VSIX indicherà che la firma non è valida. L'installazione non viene arrestata, ma l'utente viene avvisato.  
  
> [!IMPORTANT]
> A partire da 2015, i pacchetti VSIX firmati con un valore diverso dalla crittografia SHA256 verranno identificati come aventi una firma non valida. L'installazione VSIX non è bloccata, ma l'utente verrà avvisato.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Firma di un progetto VSIX con VSIXSignTool  
 È disponibile uno strumento di firma della crittografia SHA256 disponibile in [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) in NuGet.org in [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Per usare VSIXSignTool  
  
1. Aggiungere il progetto VSIX a un progetto.  
  
2. Fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni, quindi scegliere **aggiungi &#124; Gestisci pacchetti NuGet**.  Per altre informazioni su NuGet e sull'aggiunta di pacchetti NuGet, vedere [Panoramica di NuGet](/nuget/) e [gestire i pacchetti NuGet usando la finestra di dialogo](/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. Cercare VSIXSignTool da VisualStudioExtensibility e installare il pacchetto NuGet.  
  
4. È ora possibile eseguire VSIXSignTool dal percorso dei pacchetti locali del progetto. Consultare la guida della riga di comando dello strumento per lo scenario di firma (VSIXSignTool.exe/?).  
  
   Ad esempio, per firmare con un file di certificato protetto da password:  
  
   Segno di VSIXSignTool.exe/f \<certfile> /p \<password>\<VSIXfile>  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
