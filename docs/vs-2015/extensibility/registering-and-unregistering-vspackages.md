---
title: La registrazione e annullamento della registrazione di pacchetti VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8995bbb47f9a65a101256029a28313768a0b04ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526410"
---
# <a name="registering-and-unregistering-vspackages"></a>Registrazione e annullamento della registrazione di pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la registrazione e annullamento della registrazione dei pacchetti VSPackage](https://docs.microsoft.com/visualstudio/extensibility/registering-and-unregistering-vspackages).  
  
Attributi vengono utilizzati per registrare un VSPackage, ma  
  
## <a name="registering-a-vspackage"></a>La registrazione di un pacchetto VSPackage  
 È possibile usare gli attributi per controllare la registrazione dei pacchetti VSPackage gestiti. Tutte le informazioni di registrazione sono contenute in un file. pkgdef. Per altre informazioni sulla registrazione basata su file, vedere [utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 Il codice seguente viene illustrato come utilizzare gli attributi di registrazione standard per registrare il pacchetto VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Annullamento della registrazione di un'estensione  
 Se si hanno provato a numerosi pacchetti VSPackage diversi e si desidera rimuoverli dall'istanza sperimentale, è possibile eseguire semplicemente il **reimpostare** comando. Cercare **reimpostare l'istanza sperimentale di Visual Studio** nella pagina di avvio del computer in uso, o eseguire questo comando dalla riga di comando:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Se si desidera disinstallare un'estensione installata nell'istanza di sviluppo di Visual Studio, andare al **strumenti / estensioni e aggiornamenti**, trovare l'estensione e fare clic su **Disinstalla**.  
  
 Se per qualche motivo nessuno di questi metodi ha esito positivo alla disinstallazione dell'estensione, è possibile annullare la registrazione di assembly VSPackage dalla riga di comando come indicato di seguito:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)

