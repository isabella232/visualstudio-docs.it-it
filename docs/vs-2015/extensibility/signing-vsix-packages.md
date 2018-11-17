---
title: Firma di pacchetti VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56ddcae38593d35bc8a31628bf3087dc79ca25c4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732542"
---
# <a name="signing-vsix-packages"></a>Firma di pacchetti VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Assembly di estensione non è necessario essere firmato prima che possono essere eseguiti in Visual Studio, ma è buona norma eseguire questa operazione.  
  
 Se si desidera proteggere l'estensione e assicurarsi che non sia stato manomesso, è possibile aggiungere una firma digitale a un pacchetto VSIX. Quando viene firmato un progetto VSIX, il programma di installazione VSIX verrà visualizzato un messaggio che indica che è firmato, oltre a ulteriori informazioni sulla firma stessa. Se il contenuto del pacchetto VSIX è stato modificato e l'estensione VSIX non è stato firmato anche in questo caso, il programma di installazione VSIX mostrerà che la firma non è valida. L'installazione non è stato arrestato, ma l'utente viene avvisato.  
  
> [!IMPORTANT]
>  A partire 2015 pacchetti VSIX firmati con un valore diverso da crittografia SHA256 verranno identificati come avente una firma non valida. Installazione di VSIX non è bloccata, ma l'utente verrà visualizzato un avviso.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>La firma di un'estensione VSIX con VSIXSignTool  
 Strumento disponibile dalla firma una crittografia di SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) su nuget.org a [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Usare il VSIXSignTool  
  
1. Aggiungere un progetto VSIX.  
  
2. Fare clic con il pulsante destro sul nodo del progetto in Esplora soluzioni selezionando **Aggiungi &#124; Gestisci pacchetti NuGet**.  Per ulteriori informazioni sull'aggiunta di NuGet e NuGet pacchetti vedere [NuGet Overview](http://docs.nuget.org/) e [gestione di pacchetti NuGet mediante la finestra di dialogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3. Cercare VSIXSignTool da VisualStudioExtensibility e installare il pacchetto NuGet.  
  
4. È ora possibile eseguire il VSIXSignTool dal percorso locale dei pacchetti del progetto. Consultare la Guida dello strumento della riga di comando per lo scenario di firma (VSIXSignTool.exe /?).  
  
   Ad esempio da firmare con una password protetta file del certificato:  
  
   /F sign VSIXSignTool.exe \<certfile >/p \<password > \<VSIXfile >  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

