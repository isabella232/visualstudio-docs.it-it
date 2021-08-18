---
title: Specifica dei gestori di file per le estensioni di file | Microsoft Docs
description: Informazioni su come determinare quale applicazione gestisce un'estensione di file in Visual Studio SDK usando OpenWithList e OpenWithProgids.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 752d34734537d46681a3a5a116640c24adaffb41
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137574"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Definizione di handle di file per le estensioni
Esistono diversi modi per determinare l'applicazione che gestisce un file con una determinata estensione di file. I verbi OpenWithList e OpenWithProgids sono due modi per specificare i gestori di file nella voce del Registro di sistema per l'estensione di file.

## <a name="openwithlist-verb"></a>Verbo OpenWithList
 Quando si fa clic con il pulsante destro del mouse su un file Windows Explorer, viene visualizzato il **comando** Apri. Se a un'estensione sono associati più prodotti, viene visualizzato un **sottomenu Apri** con.

 È possibile registrare applicazioni diverse per aprire un'estensione impostando la chiave OpenWithList per l'estensione di file in HKEY_CLASSES_ROOT. Le applicazioni elencate in questa chiave per un'estensione di file vengono visualizzate sotto **l'intestazione Programmi** consigliati nella **finestra di dialogo** Apri con . L'esempio seguente illustra le applicazioni registrate per aprire l'estensione di file vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Le chiavi che specificano le applicazioni sono nell'elenco in HKEY_CLASSES_ROOT\Applications.

 Aggiungendo una chiave OpenWithList, si dichiara che l'applicazione supporta un'estensione di file anche se un'altra applicazione assume la proprietà dell'estensione. Potrebbe trattarsi di una versione futura dell'applicazione o di un'altra applicazione.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Gli identificatori a livello di codice (ProgID) sono versioni descrittive di ClassID che identificano una versione di un'applicazione o di un oggetto COM. Ogni oggetto co-creabile deve avere il proprio ProgID. Ad esempio, VisualStudio.DTE.7.1 avvia Visual Studio .NET 2003 mentre VisualStudio.DTE.10.0 avvia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Come proprietario di un tipo di progetto o di un tipo di elemento di progetto, è necessario creare un ProgID specifico della versione per l'estensione di file. Questi ProgID possono essere ridondanti in quanto più ProgID possono avviare la stessa applicazione. Per altre informazioni, vedere [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md).

 Usare la convenzione di denominazione seguente per i ProgID di file con versione per evitare la duplicazione con la registrazione da altri fornitori:

|Estensione file|ProgID con controllo delle versioni|
|--------------------|----------------------|
|estensione|Productname. extension.versionMajor.versionMinor|

 È possibile registrare applicazioni diverse in grado di aprire una determinata estensione di file aggiungendo progID con controllo delle versioni come valori alla chiave HKEY_CLASSES_ROOT \\ *\<extension>* \OpenWithProgids. Questa chiave del Registro di sistema contiene un elenco di ProgID alternativi associati all'estensione di file. Le applicazioni associate ai ProgID elencati vengono visualizzate nel **sottomenu Apri** con _nome prodotto._ Se la stessa applicazione viene specificata in entrambe le chiavi `OpenWithList` e , il sistema operativo unisce i `OpenWithProgids` duplicati.

> [!NOTE]
> La `OpenWithProgids` chiave è supportata solo in Windows XP. Poiché altri sistemi operativi ignorano questa chiave, non usarla come unica registrazione per i gestori di file. Usare questa chiave per offrire un'esperienza utente migliore in Windows XP.

 Aggiungere i ProgID desiderati come valori del tipo REG_NONE. Il codice seguente fornisce un esempio di registrazione di ProgID per un'estensione di file (.*ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Il ProgID specificato come valore predefinito per l'estensione di file è il gestore di file predefinito. Se si modifica ProgID per un'estensione di file fornita con una versione precedente di o che può essere utilizzata da altre applicazioni, è necessario registrare la chiave per l'estensione di file e specificare il nuovo ProgID nell'elenco insieme ai ProgID precedenti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `OpenWithProgids` supportati. Esempio:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Se al progID precedente sono associati verbi, questi verbi verranno visualizzati anche in Apri con  *nome prodotto* nel menu di scelta rapida.

## <a name="see-also"></a>Vedi anche
- [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md)
- [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)
