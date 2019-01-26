---
title: Specifica di gestori di File per estensioni di File | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1a8814ebf769ba76fe7c1dc6646248a088bc17f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982559"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Definizione di handle di file per le estensioni
Esistono diversi modi per determinare l'applicazione che gestisce un file con un'estensione di file specifico. I verbi OpenWithList e OpenWithProgids in due modi per specificare i gestori di file nella voce del Registro di sistema per l'estensione di file.  
  
## <a name="openwithlist-verb"></a>Verbo OpenWithList  
 Facendo clic su un file in Windows Explorer, vedere la **aperto** comando. Se più di un prodotto è associato a un'estensione, viene visualizzato un **aperta con** sottomenu.  
  
 È possibile registrare applicazioni diverse di aprire un'estensione impostando la chiave OpenWithList per l'estensione di file in HKEY_CLASSES_ROOT. Le applicazioni elencate in questa chiave per un'estensione di file vengono visualizzati sotto la **applicazioni consigliate** sull'intestazione nel **Apri con** nella finestra di dialogo. Nell'esempio seguente mostra le applicazioni registrate per aprire l'estensione del file con estensione vcproj.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Le chiavi che specifica le applicazioni sono nell'elenco sotto HKEY_CLASSES_ROOT\Applications.  
  
 Aggiunta di una chiave OpenWithList, si dichiara che l'applicazione supporta un'estensione di file anche se un'altra applicazione assume la proprietà dell'estensione. Potrebbe trattarsi di una versione futura dell'applicazione o un'altra applicazione.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identificatori a livello di codice (ProgID) sono versioni descrittive dei ClassID che identificano una versione di un'applicazione o un oggetto COM. Ogni oggetto generabile condiviso deve avere un proprio ProgID. Ad esempio, VisualStudio.DTE.7.1 avvia Visual Studio .NET 2003 durante l'avvio di VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Come proprietario di un tipo di progetto o un tipo di elemento di progetto, è necessario creare un ProgID specifico della versione per l'estensione di file. Questi ProgID potrebbero essere ridondanti, in quanto più di un ProgID può avviare l'applicazione stessa. Per altre informazioni, vedere [la registrazione di verbi per estensioni di File](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Usare la seguente convenzione di denominazione per il file con controllo delle versioni ProgID per evitare la duplicazione con la registrazione di altri fornitori:  
  
|Estensione di file|Con controllo delle versioni ProgID|  
|--------------------|----------------------|  
|. estensione.|ProductName. extension.versionMajor.versionMinor|  
  
 È possibile registrare diverse applicazioni che sono in grado di aprire una particolare estensione di file mediante l'aggiunta di ProgID con controllo delle versioni come valori per il HKEY_CLASSES_ROOT\\*\<estensione >* \OpenWithProgids chiave. Questa chiave del Registro di sistema contiene un elenco di ProgID alternativo associato all'estensione di file. Le applicazioni associate ai ProgID elencati vengono visualizzati nei **Apri con**_Product Name_ sottomenu. Se viene specificato dall'applicazione stessa in entrambe le `OpenWithList` e `OpenWithProgids` chiavi, il sistema operativo unisce i duplicati.  
  
> [!NOTE]
>  Il `OpenWithProgids` chiave è supportata solo in Windows XP. Poiché gli altri sistemi operativi non supportano questa chiave, non utilizzarlo come la registrazione sola per i gestori di file. Usare questa chiave per fornire una migliore esperienza utente in Windows XP.  
  
 Aggiungere i ProgID desiderati come valori del tipo REG_NONE. Il codice seguente viene fornito un esempio di registrazione ProgID per un'estensione di file (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Il valore ProgID specificato, come il valore predefinito per l'estensione del file è il gestore di file predefinito. Se si modifica il ProgID per un'estensione di file forniti con una versione precedente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o che può essere preso in carico da altre applicazioni, quindi è necessario registrare il `OpenWithProgids` la chiave per l'estensione di file e specificare il ProgID di nuovo nell'elenco insieme a gli ID di programma precedente che è supportato. Ad esempio:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Se il vecchio valore ProgID ha i verbi associati, quindi questi verbi verranno visualizzati anche in **Apri con** *Product Name* nel menu di scelta rapida.  
  
## <a name="see-also"></a>Vedere anche  
 [Sulle estensioni di File](../extensibility/about-file-name-extensions.md)   
 [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)