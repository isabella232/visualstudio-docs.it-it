---
title: 'Procedura: Creare manualmente il pacchetto estensione (distribuzione VSIX) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: e4d721fca8d429fe81de30306a8823e3d7fd9cab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681686"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Procedura: Creare manualmente il pacchetto estensione (distribuzione VSIX)
È possibile creare un pacchetto VSIX per eseguire il wrapping di un'estensione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per la distribuzione. La creazione del pacchetto può avvenire in tre modi:  
  
- Creare un progetto di pacchetto VSIX usando uno dei modelli di estendibilità inclusi in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK. Questa è l'opzione più semplice per la maggior parte degli scenari.  
  
- Eseguire il wrapping dell'output del progetto di estensione in un [progetto VSIX](../extensibility/vsix-project-template.md)vuoto. È consigliabile scegliere questa opzione per i modelli, gli assembly non supportati e i tipi personalizzati.  
  
- Creare manualmente un pacchetto VSIX. È consigliabile scegliere questa opzione solo quando le altre due opzioni non sono disponibili.  
  
  Questo documento descrive la terza opzione.  
  
## <a name="creating-a-vsix-package"></a>Creazione di un pacchetto VSIX  
 Per creare manualmente un pacchetto di un'estensione, aggiungere un file extension.manifest e un file [Content_Types].xml al progetto di estensione, inserirli in un file compresso con l'output di compilazione e rinominare il file compresso assegnandogli un'estensione di file vsix. L'estensione di cui creare il pacchetto deve essere di un tipo supportato dallo [schema VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
> I nomi dei file nei pacchetti VSIX non devono includere spazi, né caratteri riservati in identificatori URI (Uniform Resource), come definito in [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Per creare manualmente un pacchetto VSIX  
  
1. Creare un'estensione di Visual Studio di un tipo supportato dallo schema VSIX.  
  
2. Creare un file XML e assegnargli il nome `extension.vsixmanifest`.  
  
3. Compilare il file extension.vsixmanifest in base allo schema VSIX. Per un esempio di manifesto, vedere [Elemento PackageManifest (elemento radice, schema VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Creare un secondo file XML e assegnargli il nome `[Content_Types].xml`.  
  
5. Compilare il file [Content_Types] XML come specificato nella [struttura del Content_types\]File con estensione XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6. Inserire entrambi i file XML in una directory con l'estensione da distribuire.  
  
     Nel caso di un modello di progetto o di un modello di elemento, inserire il file ZIP contenente il modello nella stessa cartella dei file XML. Non inserire i file XML nel file ZIP.  
  
     In tutti gli altri casi, inserire i file XML nella stessa directory dell'output di compilazione.  
  
7. In Esplora risorse fare clic con il pulsante destro del mouse sulla cartella che include il contenuto dell'estensione e i due file XML, scegliere **Invia a**e quindi fare clic su **Cartella compressa**.  
  
8. Rinominare il file ZIP risultante in *Nomefile*.vsix, dove *Nomefile* è il nome del file ridistribuibile che installa il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Visual Studio di spedizione](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Elemento PackageManifest (elemento radice, Schema VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)