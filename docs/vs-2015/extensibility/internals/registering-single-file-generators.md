---
title: Registrazione di generatori di file singoli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696096"
---
# <a name="registering-single-file-generators"></a>Registrazione di generatori di file singoli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per rendere disponibile uno strumento personalizzato in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , è necessario registrarlo in modo che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] possa crearne un'istanza e associarlo a un determinato tipo di progetto.  
  
### <a name="to-register-a-custom-tool"></a>Per registrare uno strumento personalizzato  
  
1. Registrare la DLL dello strumento personalizzato nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Registro di sistema locale o nel registro di sistema, in HKEY_CLASSES_ROOT.  
  
     Ad esempio, di seguito sono riportate le informazioni di registrazione per lo strumento personalizzato MSDataSetGenerator personalizzato, disponibile in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. Creare una chiave del registro di sistema nell'hive desiderato in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] generatori \\ *GUID* , dove *GUID* è il GUID definito dal sistema di progetto o dal servizio del linguaggio specifico. Il nome della chiave diventa il nome a livello di codice dello strumento personalizzato. La chiave dello strumento personalizzata presenta i valori seguenti:  
  
    - Valore predefinito.  
  
         facoltativo. Fornisce una descrizione intuitiva dello strumento personalizzato. Questo parametro è facoltativo, ma consigliato.  
  
    - CLSID  
  
         Obbligatorio. Specifica l'identificatore della libreria di classi del componente COM che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  
  
    - GeneratesDesignTimeSource  
  
         Obbligatorio. Indica se i tipi dei file prodotti da questo strumento personalizzato vengono resi disponibili per le finestre di progettazione visiva. Il valore di questo parametro deve essere (zero) 0 per i tipi non disponibili per le finestre di progettazione visiva o (uno) 1 per i tipi disponibili per le finestre di progettazione visive.  
  
    > [!NOTE]
    > È necessario registrare lo strumento personalizzato separatamente per ogni lingua per cui si desidera che lo strumento personalizzato sia disponibile.  
  
     Il MSDataSetGenerator, ad esempio, si registra una sola volta per ogni lingua:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementazione di generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)   
 [Determinazione dello spazio dei nomi predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Esposizione di tipi a finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Introduzione all'oggetto BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
