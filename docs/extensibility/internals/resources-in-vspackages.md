---
title: Risorse in VSPackage . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705597"
---
# <a name="resources-in-vspackages"></a>Risorse nei pacchetti VSPackage
È possibile incorporare le risorse localizzate in DLL dell'interfaccia utente satellite native, DLL satellite gestite o in un VSPackage gestito stesso.

 Alcune risorse non possono essere incorporate nei package VS. È possibile incorporare i seguenti tipi gestiti:

- Stringhe

- Chiavi di caricamento del pacchetto (che sono anche stringhe)Package load keys (which are also strings)

- Icone della finestra degli strumenti

- File CTO (Command Table Output) compilati

- Bitmap CTO

- Guida della riga di comando

- Informazioni sui dati della finestra di dialogo

  Le risorse in un pacchetto gestito vengono selezionate in base all'ID risorsa. Un'eccezione è il file CTO, che deve essere denominato CTMENU. Il file CTO deve essere visualizzato `byte[]`nella tabella delle risorse come file . Tutti gli altri elementi risorsa sono identificati dal tipo.

  È possibile <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> utilizzare l'attributo per indicare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che le risorse gestite sono disponibili.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  L'impostazione <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] questo modo indica che ignorare le DLL satellite non gestite <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>durante la ricerca di risorse, ad esempio utilizzando . Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono rilevate due o più risorse con lo stesso ID risorsa, viene utilizzata la prima risorsa trovata.

## <a name="example"></a>Esempio
 L'esempio seguente è una rappresentazione gestita dell'icona di una finestra degli strumenti.

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

 Nell'esempio seguente viene illustrato come incorporare la matrice di byte CTO, che deve essere denominata CTMENU.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ritarda il caricamento dei pacchetti VSPackage quando possibile. Una conseguenza dell'incorporamento di un file [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] CTO in un VSPackage è che è necessario caricare tutti i pacchetti VSPackage in memoria durante l'installazione, ovvero quando viene compilata una tabella di comando unita. Le risorse possono essere estratte da un pacchetto VSPackage esaminando i metadati senza eseguire codice nel pacchetto VSPackage.Resources can be extracted from a VSPackage by examining the metadata without running code in the VSPackage. Il pacchetto VSPackage non viene inizializzato in questo momento, pertanto la perdita di prestazioni è minima.

 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede una risorsa da un VSPackage dopo l'installazione, è probabile che tale pacchetto sia già caricato e inizializzato, pertanto la perdita di prestazioni è minima.

## <a name="see-also"></a>Vedere anche
- [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)
- [Risorse localizzate in applicazioni MFC: DLL satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
