---
title: Specifica dei gestori di file per le estensioni di file | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699747"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Definizione di handle di file per le estensioni
Esistono diversi modi per determinare l'applicazione che gestisce un file con una specifica estensione di file. I verbi OpenWithList e OpenWithProgids sono due modi per specificare i gestori di file nella voce del registro di sistema per l'estensione di file.

## <a name="openwithlist-verb"></a>Verbo OpenWithList
 Quando si fa clic con il pulsante destro del mouse su un file in Esplora risorse, viene visualizzato il comando **Apri** . Se a un'estensione è associato più di un prodotto, viene visualizzato un sottomenu **Apri con** .

 È possibile registrare diverse applicazioni per aprire un'estensione impostando la chiave OpenWithList per l'estensione di file in HKEY_CLASSES_ROOT. Le applicazioni elencate in questa chiave per un'estensione di file vengono visualizzate sotto l'intestazione **Programmi consigliati** nella finestra **di dialogo Apri con** . Nell'esempio seguente vengono illustrate le applicazioni registrate per aprire l'estensione di file. vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Le chiavi che specificano le applicazioni sono incluse nell'elenco HKEY_CLASSES_ROOT \Applications.

 Aggiungendo una chiave OpenWithList, si dichiara che l'applicazione supporta un'estensione di file anche se un'altra applicazione acquisisce la proprietà dell'estensione. Potrebbe trattarsi di una versione futura dell'applicazione o di un'altra applicazione.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Gli identificatori a livello di codice (ProgID) sono versioni descrittiva di ClassID che identificano una versione di un'applicazione o di un oggetto COM. Ogni oggetto co-creabile deve avere il proprio ProgID. Ad esempio, VisualStudio. DTE. 7.1 avvia Visual Studio .NET 2003 mentre VisualStudio. DTE. 10.0 viene avviato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Come proprietario di un tipo di progetto o di un tipo di elemento di progetto, è necessario creare un ProgID specifico della versione per l'estensione di file. Questi ProgID potrebbero essere ridondanti in quanto più ProgID possono avviare la stessa applicazione. Per ulteriori informazioni, vedere la pagina relativa alla [registrazione dei verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md).

 Usare la convenzione di denominazione seguente per i ProgID dei file con versione per evitare la duplicazione con la registrazione di altri fornitori:

|Estensione file|ProgID con versione|
|--------------------|----------------------|
|estensione|ProductName. estensione. Proprietà VersionMajor. versionMinor|

 È possibile registrare diverse applicazioni in grado di aprire un'estensione di file specifica aggiungendo ProgID con versione come valori alla chiave di HKEY_CLASSES_ROOT \\ *\<extension>* \OpenWithProgids. Questa chiave del registro di sistema contiene un elenco di ProgID alternativi associati all'estensione di file. Le applicazioni associate ai ProgID elencati vengono visualizzate nel sottomenu **Apri con**_nome prodotto_ . Se la stessa applicazione viene specificata in entrambe le `OpenWithList` `OpenWithProgids` chiavi e, il sistema operativo unisce i duplicati.

> [!NOTE]
> La `OpenWithProgids` chiave è supportata solo in Windows XP. Poiché altri sistemi operativi ignorano questa chiave, non usarla come unica registrazione per i gestori di file. Usare questa chiave per offrire una migliore esperienza utente in Windows XP.

 Aggiungere i ProgID desiderati come valori del tipo REG_NONE. Il codice seguente fornisce un esempio di registrazione dei ProgID per un'estensione di file (.* EXT*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Il ProgID specificato come valore predefinito per l'estensione di file è il gestore di file predefinito. Se si modifica il ProgID per un'estensione di file fornita con una versione precedente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o che può essere rilevata da altre applicazioni, è necessario registrare la `OpenWithProgids` chiave per l'estensione di file e specificare il nuovo ProgID nell'elenco insieme ai ProgID precedenti supportati. Ad esempio:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Se al ProgID precedente sono associati verbi, questi verbi verranno visualizzati anche in **Apri con** *nome prodotto* nel menu di scelta rapida.

## <a name="see-also"></a>Vedere anche
- [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md)
- [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)
