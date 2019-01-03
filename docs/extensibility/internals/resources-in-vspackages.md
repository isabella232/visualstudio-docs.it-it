---
title: Le risorse nei pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6bacf652d1fd691f17e721851b5b49d0da7acca0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827494"
---
# <a name="resources-in-vspackages"></a>Risorse nei pacchetti VSPackage
È possibile incorporare le risorse localizzate in nativa dell'interfaccia utente le DLL satellite, le DLL satellite gestite, o in un pacchetto VSPackage gestito se stesso.  
  
 Alcune risorse non è possibile incorporare nei pacchetti VSPackage. I seguenti tipi gestiti possono essere incorporati:  
  
- Stringhe  
  
- Chiavi di caricamento package (che sono anche le stringhe)  
  
- Icone della finestra degli strumenti  
  
- File di Output di tabella comandi (CTO) compilati  
  
- Bitmap CTO  
  
- Guida della riga di comando  
  
- Sui dati della finestra di dialogo  
  
  Selezionare le risorse in un pacchetto gestito dall'ID di risorsa. Un'eccezione è il file CTO, che deve essere denominato CTMENU. Il file CTO deve essere visualizzato nella tabella delle risorse come un `byte[]`. Tutti gli altri elementi risorsa vengono identificate dal tipo.  
  
  È possibile usare la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> attributo per indicare al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che siano disponibili le risorse gestite.  
  
  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
  L'impostazione <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> indica che in questo modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve ignorare le DLL satellite non gestita durante la ricerca di risorse, ad esempio, usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva due o più risorse aventi lo stesso ID di risorsa, Usa la prima risorsa trovata.  
  
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
  
 Nell'esempio seguente viene illustrato come incorporare la matrice di byte CTO, deve chiamarsi CTMENU.  
  
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
  
## <a name="implementation-notes"></a>Note di implementazione  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricamento dei ritardi di VSPackage laddove possibile. Una conseguenza dell'incorporamento di un file CTO in un pacchetto VSPackage è che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] necessario caricare tutti questi pacchetti VSPackage in memoria durante l'installazione, ovvero quando compila una tabella comandi unite. Le risorse possono essere estratti da un pacchetto VSPackage esaminando i metadati senza eseguire codice nel pacchetto VSPackage. Il pacchetto VSPackage non è inizializzato a questo punto, in modo che la riduzione delle prestazioni è minima.  
  
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richieste una risorsa da un pacchetto VSPackage al termine dell'installazione, tale pacchetto è probabilmente già caricato e inizializzato, in modo che la riduzione delle prestazioni è minima.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)   
 [Risorse localizzate in applicazioni MFC: DLL satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
