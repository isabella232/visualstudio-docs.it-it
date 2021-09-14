---
title: Risorse nei pacchetti VSPackage | Microsoft Docs
description: Informazioni sui tipi di risorse localizzate che è possibile incorporare in VSPackage. È anche possibile incorporare risorse in DLL dell'interfaccia utente satellite native o DLL satellite gestite.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 87ebfb777aed483fefbf5d4c3caeee8587c41b03
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709501"
---
# <a name="resources-in-vspackages"></a>Risorse nei pacchetti VSPackage
È possibile incorporare risorse localizzate in DLL dell'interfaccia utente satellite native, DLL satellite gestite o in un VSPackage gestito.

 Alcune risorse non possono essere incorporate in VSPackage. È possibile incorporare i tipi gestiti seguenti:

- Stringhe

- Chiavi di caricamento del pacchetto (che sono anche stringhe)

- Icone della finestra degli strumenti

- File CTO (Command Table Output) compilati

- Bitmap CTO

- Guida della riga di comando

- Informazioni sui dati della finestra di dialogo

  Le risorse in un pacchetto gestito vengono selezionate in base all'ID risorsa. Un'eccezione è il file CTO, che deve essere denominato CTMENU. Il file CTO deve essere visualizzato nella tabella delle risorse come `byte[]` . Tutti gli altri elementi della risorsa sono identificati dal tipo.

  È possibile usare <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> l'attributo per indicare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che le risorse gestite sono disponibili.

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs" id="Snippet1":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb" id="Snippet1":::

  L'impostazione in questo modo indica che le DLL satellite non gestite devono essere ignorate durante la ricerca di risorse, ad esempio <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva due o più risorse con lo stesso ID risorsa, usa la prima risorsa trovata.

## <a name="example"></a>Esempio
 L'esempio seguente è una rappresentazione gestita di un'icona della finestra degli strumenti.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 L'esempio seguente illustra come incorporare la matrice di byte CTO, che deve essere denominata CTMENU.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Note sull'implementazione
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ritarda il caricamento di VSPackage quando possibile. Una conseguenza dell'incorporamento di un file CTO in un VSPackage è che deve caricare tutti questi VSPackage in memoria durante l'installazione, ovvero quando compila una tabella dei comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unita. Le risorse possono essere estratte da un pacchetto VSPackage esaminando i metadati senza eseguire codice nel pacchetto VSPackage. Il pacchetto VSPackage non viene inizializzato in questo momento, quindi la perdita di prestazioni è minima.

 Quando richiede una risorsa da un pacchetto VSPackage dopo l'installazione, è probabile che il pacchetto sia già caricato e inizializzato, quindi la perdita di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prestazioni è minima.

## <a name="see-also"></a>Vedi anche
- [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)
- [Risorse localizzate nelle applicazioni MFC: DLL satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
