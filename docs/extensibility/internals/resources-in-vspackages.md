---
title: Risorse nei pacchetti VSPackage | Microsoft Docs
description: Informazioni sui tipi di risorse localizzate che possono essere incorporati nei pacchetti VSPackage. È anche possibile incorporare risorse in DLL dell'interfaccia utente satellite native o dll satellite gestite.
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
ms.workload:
- vssdk
ms.openlocfilehash: c4863fb40bc6f70556d8f00305d882e6edd93a0e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074392"
---
# <a name="resources-in-vspackages"></a>Risorse nei pacchetti VSPackage
È possibile incorporare le risorse localizzate in DLL dell'interfaccia utente satellite nativa, dll satellite gestite o in un VSPackage gestito.

 Non è possibile incorporare alcune risorse nei pacchetti VSPackage. È possibile incorporare i tipi gestiti seguenti:

- Stringhe

- Chiavi di caricamento del pacchetto (stringhe anche)

- Icone della finestra degli strumenti

- File di output della tabella dei comandi (CTO) compilati

- Bitmap CTO

- Guida della riga di comando

- Informazioni sui dati della finestra di dialogo

  Le risorse in un pacchetto gestito sono selezionate in base all'ID risorsa. Un'eccezione è il file CTO, che deve essere denominato CTMENU. Il file CTO deve essere visualizzato nella tabella Resource come `byte[]` . Tutti gli altri elementi di risorsa sono identificati dal tipo.

  È possibile utilizzare l' <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> attributo per indicare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che sono disponibili risorse gestite.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>L'impostazione in questo modo indica che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve ignorare le DLL satellite non gestite durante la ricerca di risorse, ad esempio tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Se rileva [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] due o più risorse con lo stesso ID di risorsa, viene usata la prima risorsa trovata.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene rappresentata una rappresentazione gestita di un'icona della finestra degli strumenti.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ritarda il caricamento dei pacchetti VSPackage laddove possibile. Una conseguenza dell'incorporamento di un file CTO in un pacchetto VSPackage è che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve caricare tutti i pacchetti VSPackage in memoria durante l'installazione, ovvero quando viene compilata una tabella dei comandi unita. Le risorse possono essere estratte da un pacchetto VSPackage esaminando i metadati senza eseguire codice nel pacchetto VSPackage. Il pacchetto VSPackage non è inizializzato in questo momento, quindi la perdita di prestazioni è minima.

 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede una risorsa da un VSPackage dopo l'installazione, è probabile che il pacchetto sia già caricato e inizializzato, quindi la perdita di prestazioni è minima.

## <a name="see-also"></a>Vedi anche
- [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)
- [Risorse localizzate in applicazioni MFC: dll satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
