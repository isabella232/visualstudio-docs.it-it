---
title: 'IDebugProgramNode2:: GetHostName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostName
helpviewer_keywords:
- IDebugProgramNode2::GetHostName
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 028ee16e7b9c5a30effc683494f68b2bd4eb604f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722062"
---
# <a name="idebugprogramnode2gethostname"></a>IDebugProgramNode2::GetHostName
Ottiene il nome del processo che ospita il programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHostName (
    GETHOSTNAME_TYPE dwHostNameType,
    BSTR*            pbstrHostName
);
```

```csharp
int GetHostName (
    enum_GETHOSTNAME_TYPE dwHostNameType,
    out string            pbstrHostName
);
```

## <a name="parameters"></a>Parametri
`dwHostNameType`\
in Valore dell'enumerazione [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) che specifica il tipo di nome da restituire.

`pbstrHostName`\
out Restituisce il nome del processo di hosting.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un `CProgram` oggetto semplice che espone l'interfaccia [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . Questo esempio ignora il `dwHostNameType` parametro e restituisce solo il nome del programma come tratto dal nome di base del percorso del file del modulo.

```cpp
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {
    // Check for valid argument.
    if (pbstrHostName)
    {
        char szModule[_MAX_PATH];

        // Attempt to assign to szModule the path for the file used
        // to create the calling process.
        if (GetModuleFileName(NULL, szModule, sizeof (szModule)))
        {
            // If successful then declare several char arrays
            char  szDrive[_MAX_DRIVE];
            char  szDir[_MAX_DIR];
            char  szName[_MAX_FNAME];
            char  szExt[_MAX_EXT];
            char  szFilename[_MAX_FNAME + _MAX_EXT];
            WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];

            // Break the szModule path name into components.
            _splitpath(szModule, szDrive, szDir, szName, szExt);

            // Copy the base file name szName into szFilename.
            lstrcpy(szFilename, szName);
            // Append the field extension szExt into szFilename.
            lstrcat(szFilename, szExt);

            // Convert the szFilename sequence of multibyte characters
            // to the wszFilename sequence of wide characters.
            mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);

            // Assign the wszFilename to the value at *pbstrHostName.
            *pbstrHostName = SysAllocString(wszFilename);

            return S_OK;
        }
    }

    return E_INVALIDARG;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
