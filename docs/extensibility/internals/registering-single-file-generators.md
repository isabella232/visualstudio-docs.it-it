---
title: Registrazione di singoli generatori di file | Microsoft Docs
description: Informazioni su come registrare uno strumento personalizzato in Visual Studio crearne un'istanza e associarlo a un particolare tipo di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ad56731f0e0432dea2eb583d23dcf4285801e2f6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062961"
---
# <a name="registering-single-file-generators"></a>Registrazione di generatori di file singoli
Per rendere disponibile uno strumento personalizzato in , è necessario registrarlo in modo da poterne creare un'istanza e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] associarlo a un particolare tipo di progetto.

### <a name="to-register-a-custom-tool"></a>Per registrare uno strumento personalizzato

1. Registrare la DLL dello strumento personalizzato nel Registro di sistema locale o nel Registro di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sistema, in HKEY_CLASSES_ROOT.

    Ecco ad esempio le informazioni di registrazione per lo strumento personalizzato MSDataSetGenerator gestito, fornito con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Creare una chiave del Registro di sistema nell'hive desiderato in GUID generatori, dove GUID è il GUID definito dal sistema di progetto o dal servizio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \\  del linguaggio specifico.  Il nome della chiave diventa il nome a livello di codice dello strumento personalizzato. La chiave dello strumento personalizzato ha i valori seguenti:

   - Valore predefinito.

        facoltativo. Fornisce una descrizione semplice dello strumento personalizzato. Questo parametro è facoltativo, ma consigliato.

   - CLSID

        Obbligatorio. Specifica l'identificatore della libreria di classi del componente COM che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

   - GeneraDesignTimeSource

        Obbligatorio. Indica se i tipi di file prodotti da questo strumento personalizzato vengono resi disponibili per le finestre di progettazione visiva. Il valore di questo parametro deve essere (zero) 0 per i tipi non disponibili per le finestre di progettazione visiva o (uno) 1 per i tipi disponibili per le finestre di progettazione visiva.

   > [!NOTE]
   > È necessario registrare lo strumento personalizzato separatamente per ogni lingua per cui si vuole che lo strumento personalizzato sia disponibile.

    Ad esempio, MSDataSetGenerator si registra una sola volta per ogni lingua:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementazione di generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)
- [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Introduzione all'oggetto BuildManager](/previous-versions/8f9kffa8(v=vs.140))