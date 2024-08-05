<script>
  import { getContext } from "svelte"

  export let data
  export let id
  export let title
  export let desciption
  export let label1
  export let additional1
  export let label2
  export let additional2
  export let label3
  export let additional3
  export let label4
  export let additional4

  const arrow = '<svg version="1.1" width="15" height="15" viewBox="0 0 512 512" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M383.6,322.7L278.6,423c-5.8,6-13.7,9-22.4,9c-8.7,0-16.5-3-22.4-9L128.4,322.7c-12.5-11.9-12.5-31.3,0-43.2  c12.5-11.9,32.7-11.9,45.2,0l50.4,48.2v-217c0-16.9,14.3-30.6,32-30.6c17.7,0,32,13.7,32,30.6v217l50.4-48.2  c12.5-11.9,32.7-11.9,45.2,0C396.1,291.4,396.1,310.7,383.6,322.7z" fill="currentColor"/></svg>'

  const { styleable } = getContext("sdk")
  const component = getContext("component")

// SORTING SECTION
// ---
  // Sorting order and active column info
  $: sortingStatus = {
    order: "ASC",
    sortedBy: "last_edit",
  }

  // Sorting function
  const sortBy = sortingSource => {
    let sortBy = sortingSource

    // Custom field detecting
    if (sortingSource === 'specialRiskValue') {
      sortBy = 'value'
    }

    // Custom field detecting
    if (sortingSource === 'specialDateTime') {
      sortBy = 'last_edit'
    }

    if (sortingStatus.order === "ASC") {
      repeaterData.sort((a, b) => {
        if (a[sortBy] < b[sortBy]) return -1;
        if (a[sortBy] > b[sortBy]) return 1;
        return 0;
      });
    } else {
      repeaterData.sort((a, b) => {
        if (a[sortBy] < b[sortBy]) return 1;
        if (a[sortBy] > b[sortBy]) return -1;
        return 0;
      });
    }

    sortingStatus.order = sortingStatus.order === "ASC" ? "DESC" : "ASC";

    sortingStatus.sortedBy = sortingSource
    repeaterData = [...repeaterData]
  }
// ---
// END SORTING SECTION

data = [
  {
    "risk_api_id": "8d7637ca-3351-48ca-ae85-6a0eb38ca36c",
    "Impact": "",
    "Status": "Monitored",
    "last_edit": "2024-08-01T07:49:21.753Z",
    "Risk": "New security risk",
    "id": 24,
    "Likelihood": "",
    "Tasks_text": "11",
    "Description": "Create new risk 23.07\n\nChecking risk ID\n\nchecking history tab\n\nChecking risk owner",
    "Comments": "eyJtZXNzYWdlIjoiVGVzdGluZyAwMS4wOCIsImVtYWlsIjoiYWlnYXJzLnNrdWx0ZUBwZWFrZGVmZW5jZS5jb20iLCJuYW1lIjoiQWlnYXJzIFNrdWx0ZSIsInRpbWVzdGFtcCI6MTcyMjQ5ODUzNjQ2NH0=",
    "_id": "%5B24%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Plans": [
      {
        "_id": "%5B4%5D",
        "primaryDisplay": "New Plan"
      },
      {
        "_id": "%5B5%5D",
        "primaryDisplay": "New"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B39%5D",
        "primaryDisplay": "11"
      }
    ],
    "Assets": [
      {
        "_id": "%5B3%5D",
        "primaryDisplay": "Google Workspace Apps"
      }
    ],
    "Controls": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      }
    ],
    "value": "6",
    "Plans_text": "New Plan, New",
    "Assets_text": "Google Workspace Apps",
    "Controls_text": "Information Security Policy"
  },
  {
    "risk_api_id": "0e0f254f-bb47-423f-9f35-0049383455e3",
    "Impact": "1",
    "Status": "Being Treated",
    "last_edit": "2024-08-02T11:37:38.895Z",
    "Risk": "New testing risk",
    "id": 26,
    "Likelihood": "2",
    "Tasks_text": "Risk 1 - new task testing",
    "Description": "Create new testing risk 01.08",
    "fk_People_Risks": 1,
    "_id": "%5B26%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "juris@peakdefence.com"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B43%5D",
        "primaryDisplay": "Risk 1 - new task testing"
      }
    ],
    "Assets": [
      {
        "_id": "%5B10%5D",
        "primaryDisplay": "New testing asset"
      },
      {
        "_id": "%5B3%5D",
        "primaryDisplay": "Google Workspace Apps"
      }
    ],
    "value": "2",
    "Owner_text": "juris@peakdefence.com",
    "Assets_text": "New testing asset, Google Workspace Apps"
  },
  {
    "risk_api_id": "7d5b8bda-677b-464e-8134-767be389ab86",
    "Impact": "1",
    "Status": "Draft",
    "last_edit": "2024-07-21T09:39:34.695Z",
    "Risk": "Phishing Attack",
    "id": 15,
    "Likelihood": "2",
    "Tasks_text": "Audit Plan",
    "Description": "Deceptive emails or messages trick users into revealing sensitive information. ",
    "fk_People_Risks": 2,
    "_id": "%5B15%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B4%5D",
        "primaryDisplay": "New Plan"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      }
    ],
    "Assets": [
      {
        "_id": "%5B4%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN Source code"
      }
    ],
    "Controls": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      }
    ],
    "value": "2",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "New Plan",
    "Assets_text": "PEAK DEFENCE WINGMAN Source code",
    "Controls_text": "Information Security Policy"
  },
  {
    "risk_api_id": "f39c0630-9c8e-4317-b328-8ca4b3206cd3",
    "Impact": "3",
    "Status": "Being Treated",
    "last_edit": "2024-08-02T14:04:06.128Z",
    "Risk": "Weak Passwords",
    "id_old": "assa",
    "id": 19,
    "Likelihood": "3",
    "Tasks_text": "Audit Plan, BCDR test run",
    "Description": "Easily guessable passwords that can be exploited by attackers to gain unauthorized access.\n[links](https://peakdefence.com) 12",
    "Comments": "eyJtZXNzYWdlIjoiTXkgY29tbWVudCIsImVtYWlsIjoianVyaXNAcGVha2RlZmVuY2UuY29tIiwibmFtZSI6Ikp1cmlzIFB1Y2UiLCJ0aW1lc3RhbXAiOjE3MjE2NjM4NzUwNjl9",
    "fk_People_Risks": 2,
    "_id": "%5B19%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Policy update"
      },
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "Threats Analysis"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      },
      {
        "_id": "%5B26%5D",
        "primaryDisplay": "BCDR test run"
      }
    ],
    "Assets": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN"
      }
    ],
    "Controls": [
      {
        "_id": "%5B3%5D",
        "primaryDisplay": "Document Management Policy "
      },
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      }
    ],
    "value": "9",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "Policy update, Threats Analysis",
    "Assets_text": "PEAK DEFENCE WINGMAN",
    "Controls_text": "Document Management Policy , Information Security Policy"
  },
  {
    "risk_api_id": "a057ad0b-490d-427b-a101-7b3f8f3fa7d1",
    "Impact": "2",
    "Status": "Draft",
    "last_edit": "2024-07-21T09:39:21.385Z",
    "Risk": "Insider Threat",
    "id": 17,
    "Likelihood": "2",
    "Tasks_text": "Audit Plan",
    "Description": "Employees or contractors misusing access for malicious purposes.",
    "fk_People_Risks": 2,
    "_id": "%5B17%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Policy update"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      }
    ],
    "Assets": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN"
      }
    ],
    "Controls": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      }
    ],
    "value": "4",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "Policy update",
    "Assets_text": "PEAK DEFENCE WINGMAN",
    "Controls_text": "Information Security Policy"
  },
  {
    "risk_api_id": "c7b72a90-9d5a-4120-a40f-34b8161b4952",
    "Impact": "1",
    "Status": "Draft",
    "last_edit": "2024-07-21T09:39:02.956Z",
    "Risk": "Malware Infection",
    "id": 16,
    "Likelihood": "2",
    "Tasks_text": "Audit Plan",
    "Description": "Malicious software like viruses and ransomware can steal data or damage systems.",
    "fk_People_Risks": 2,
    "_id": "%5B16%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "Threats Analysis"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      }
    ],
    "Assets": [
      {
        "_id": "%5B4%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN Source code"
      }
    ],
    "Controls": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      }
    ],
    "value": "2",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "Threats Analysis",
    "Assets_text": "PEAK DEFENCE WINGMAN Source code",
    "Controls_text": "Information Security Policy"
  },
  {
    "risk_api_id": "166d8b1f-4bc9-4b41-b277-adc3b084e953",
    "Impact": "3",
    "Status": "Draft",
    "last_edit": "2024-08-02T13:04:57.489Z",
    "id": 27,
    "Likelihood": "2",
    "Description": "Missed Documentation",
    "_id": "%5B27%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "value": "6"
  },
  {
    "risk_api_id": "b77bfcf7-a052-44b9-bacd-1f3c4596da2f",
    "Impact": "1",
    "last_edit": "2024-08-02T22:39:28.465Z",
    "Risk": "Electricity overload",
    "id": 43,
    "Likelihood": "4",
    "Description": "Not enough of electricity power",
    "_id": "%5B43%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "value": "4"
  },
  {
    "risk_api_id": "c4da4f46-351d-4454-8a3c-1b0bc1b7d85c",
    "Impact": "2",
    "Status": "Draft",
    "last_edit": "2024-07-21T09:39:13.522Z",
    "Risk": "Unpatched Software",
    "id": 20,
    "Likelihood": "3",
    "Tasks_text": "Audit Plan, BCDR test run",
    "Description": "Outdated software with vulnerabilities that can be exploited by attackers.",
    "fk_People_Risks": 2,
    "_id": "%5B20%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "Threats Analysis"
      },
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Policy update"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      },
      {
        "_id": "%5B26%5D",
        "primaryDisplay": "BCDR test run"
      }
    ],
    "Assets": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN"
      }
    ],
    "Controls": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      },
      {
        "_id": "%5B3%5D",
        "primaryDisplay": "Document Management Policy "
      }
    ],
    "value": "6",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "Threats Analysis, Policy update",
    "Assets_text": "PEAK DEFENCE WINGMAN",
    "Controls_text": "Information Security Policy, Document Management Policy "
  },
  {
    "risk_api_id": "32588ac9-8b34-4bbb-83d8-d92b12103057",
    "Impact": "2",
    "Status": "Being Treated",
    "last_edit": "2024-07-23T12:22:02.286Z",
    "Risk": "Security mechanism",
    "id": 23,
    "Likelihood": "3",
    "Description": "Security mechanism",
    "fk_People_Risks": 1,
    "_id": "%5B23%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "juris@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Policy update"
      },
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "Threats Analysis"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B39%5D",
        "primaryDisplay": "11"
      },
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      }
    ],
    "Assets": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN"
      }
    ],
    "value": "6",
    "Owner_text": "juris@peakdefence.com",
    "Plans_text": "Policy update, Threats Analysis",
    "Tasks_text": "11, Audit Plan",
    "Assets_text": "PEAK DEFENCE WINGMAN"
  },
  {
    "risk_api_id": "6fce7317-ac11-427c-b33c-616d3182aec6",
    "Impact": "2",
    "Status": "Draft",
    "last_edit": "2024-07-23T12:21:32.715Z",
    "Risk": "Security mechanism",
    "id": 22,
    "Likelihood": "2",
    "Description": "Security mechanism",
    "fk_People_Risks": 2,
    "_id": "%5B22%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Policy update"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B26%5D",
        "primaryDisplay": "BCDR test run"
      },
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "Document organisational structure, roles and responsibilities."
      }
    ],
    "Assets": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN"
      }
    ],
    "value": "4",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "Policy update",
    "Tasks_text": "BCDR test run, Document organisational structure, roles and responsibilities.",
    "Assets_text": "PEAK DEFENCE WINGMAN"
  },
  {
    "risk_api_id": "48e97047-eb03-43e6-b79e-768cd72a1d0f",
    "Impact": "2",
    "Status": "Being Treated",
    "last_edit": "2024-08-02T11:11:56.951Z",
    "Risk": "Malware Infection by user",
    "id": 21,
    "Likelihood": "4",
    "Tasks_text": "Audit Plan, BCDR test run",
    "Description": "Software with malicious logic that can steal confidential data",
    "fk_People_Risks": 2,
    "_id": "%5B21%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Policy update"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      },
      {
        "_id": "%5B26%5D",
        "primaryDisplay": "BCDR test run"
      }
    ],
    "Assets": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN"
      }
    ],
    "Controls": [
      {
        "_id": "%5B3%5D",
        "primaryDisplay": "Document Management Policy "
      },
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      }
    ],
    "value": "8",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "Policy update",
    "Assets_text": "PEAK DEFENCE WINGMAN",
    "Controls_text": "Document Management Policy , Information Security Policy"
  },
  {
    "risk_api_id": "16c966ed-0733-4363-b2ae-8c77cd750c79",
    "Impact": "2",
    "Status": "Draft",
    "last_edit": "2024-07-25T16:38:05.013Z",
    "id": 25,
    "Likelihood": "2",
    "Description": "System updates (e.g. Malware signatures and malware protection drivers) can lead to system downtime due to misconfigurations.",
    "fk_People_Risks": 1,
    "_id": "%5B25%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "juris@peakdefence.com"
      }
    ],
    "value": "4",
    "Owner_text": "juris@peakdefence.com"
  },
  {
    "risk_api_id": "67aff362-46b0-43d5-af9c-118138a3e296",
    "Impact": "2",
    "Status": "Draft",
    "last_edit": "2024-07-21T09:39:45.582Z",
    "Risk": "Data Breaches",
    "id": 18,
    "Likelihood": "3",
    "Tasks_text": "BCDR test run, Audit Plan",
    "Description": "Unauthorized access to sensitive data, leading to exposure and potential misuse.",
    "fk_People_Risks": 2,
    "_id": "%5B18%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "roman@peakdefence.com"
      }
    ],
    "Plans": [
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "Threats Analysis"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B26%5D",
        "primaryDisplay": "BCDR test run"
      },
      {
        "_id": "%5B29%5D",
        "primaryDisplay": "Audit Plan"
      }
    ],
    "Assets": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "PEAK DEFENCE WINGMAN"
      }
    ],
    "Controls": [
      {
        "_id": "%5B2%5D",
        "primaryDisplay": "Information Security Policy"
      }
    ],
    "value": "6",
    "Owner_text": "roman@peakdefence.com",
    "Plans_text": "Threats Analysis",
    "Assets_text": "PEAK DEFENCE WINGMAN",
    "Controls_text": "Information Security Policy"
  },
  {
    "risk_api_id": "69b5e359-3d3a-4ca6-b733-f01c73d136b9",
    "Impact": "2",
    "Status": "Being Treated",
    "last_edit": "2024-08-02T14:07:45.159Z",
    "Risk": "Dangerous animals",
    "id": 28,
    "Likelihood": "2",
    "Tasks_text": "Add owner",
    "Description": "Wild animals attacking employees",
    "fk_People_Risks": 1,
    "_id": "%5B28%5D",
    "tableId": "datasource_plus_f4f5852a470d4c7bbe38b520da6e5c5b__Risks",
    "_rev": "rev",
    "Owner": [
      {
        "_id": "%5B1%5D",
        "primaryDisplay": "juris@peakdefence.com"
      }
    ],
    "Tasks": [
      {
        "_id": "%5B32%5D",
        "primaryDisplay": "Add owner"
      }
    ],
    "value": "4",
    "Owner_text": "juris@peakdefence.com"
  }
]

// CUSTOM FIELDS SECTION
  // Adding of a value field, which does not come from Budibase
  const initialData = data.map(i => {
    return {
      ...i,
      value: i.Likelihood * i.Impact
    };
  });

  $: repeaterData = initialData;
  // Expected keys:
  // 'specialRiskValue': Computed field by "likelihood" and "Impact" values and colored by priority
  // 'specialDateTime': UI friendly parsed Date (YYYY.MM.DD HH:mm)
  const fieldParser = function (value, key) {
    if (key === "specialRiskValue") {
      return specialRiskValueBuilder(value, 'html')
    } else if (key === "specialDateTime") {
      return specialDateTimeBuilder(value)
    }
    
    if (typeof value[key] === 'object') {
      return value[key][0].primaryDisplay;
      // return value[key].primaryDisplay ? value[key].primaryDisplay : '-'
    }

    return value[key] ? value[key] : '-'
  }

  const specialRiskValueBuilder = function (value, view) {
    let riskValue = value.Impact * value.Likelihood

    let bgColor;

    const detectScore = (value) => {
      if (value < 4 && value > 0) {
        bgColor = '#2eb85c';
      } else if (value > 3 && value <=7) {
        bgColor = '#f8b114';
      } else if (value > 7) {
        bgColor = '#e45353';
      } else if (!value) {
        bgColor = '#CED4DA'
        riskValue = '-'
      }
    };

    detectScore(riskValue);

    const htmlResult = '<div style="display: inline-block; width: 60px; line-height: 30px;' +
      'text-align: center;' + 
      'color: #fff;' +
      'border-radius: 4px;' +
      'background-color: ' + bgColor +
    ';">' + riskValue + '</div>'

    return view === 'html' ? htmlResult : riskValue
  }

  const specialDateTimeBuilder = function (value) {
    const dateString = value.last_edit

    const [datePart, timePart] = dateString.split("T")
    let [year, month, day] = datePart.split("-").map(String)
    let [hours, minutes] = timePart.split(":").map(String)

    day = day.length < 2 ? "0" + day : day
    month = month.length < 2 ? "0" + month : month

    return `${day}.${month}.${year} ${hours}:${minutes}`
  }
// END CUSTOM FIELDS SECTION

// ACTIONS
  // Link to item card page
  const moveToCard = function (id) {
    const targetUrl = window.location.href + `/${id}`
    window.location.href = targetUrl
  }
// END ACTIONS
</script>

<div use:styleable={$component.styles}>
  {#if repeaterData.length > 0}
  <ul class="data-list">
    <li class="data-item data-item-header sorting-row {sortingStatus.order === "ASC" ? 'sorted-by-asc' : 'sorted-by-desc'}">
      {#if id}
        <span class="data-column data-column-general">
          <button class="sorting-item {sortingStatus.sortedBy === id ? 'is-active' : ''}" on:click={sortBy(id)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional1}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional1 ? 'is-active' : ''}" on:click={sortBy(additional1)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional2}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional2 ? 'is-active' : ''}" on:click={sortBy(additional2)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional3}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional3 ? 'is-active' : ''}" on:click={sortBy(additional3)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional4}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional4 ? 'is-active' : ''}" on:click={sortBy(additional4)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
    </li>
    {#each repeaterData as item, index}
      <li
        class="data-item"
        on:click={moveToCard(item.id)}
        on:keydown={(event) => moveToCard(event, item.id)}
      >
        <div class="data-column data-column-general">
          <strong class="data-column-label">#{item[id]}</strong>
          {#if item[title]}
            <h5 class="data-item-title">{item[title]}</h5>
          {/if}
          <span class="data-column-data">{item[desciption]}</span>
        </div>
        {#if additional1}
          <div class="data-column">
            <strong class="data-column-label">{label1}</strong>
            <span class="data-column-data">{fieldParser(item, additional1, index)}</span>
          </div>
        {/if}
        {#if additional2}
          <div class="data-column">
            <strong class="data-column-label">{label2}</strong>
            <span class="data-column-data">{@html fieldParser(item, additional2, index)}</span>
          </div>
        {/if}
        {#if additional3}
          <div class="data-column">
            <strong class="data-column-label">{label3}</strong>
            <span class="data-column-data">{fieldParser(item, additional3, index)}</span>
          </div>
        {/if}
        {#if additional4}
          <div class="data-column">
            <strong class="data-column-label">{label4}</strong>
            <span class="data-column-data">{fieldParser(item, additional4, index)}</span>
          </div>
        {/if}
      </li>
    {/each}
  </ul>
  {:else}
    <p class="no-items">No items in the list.</p>
  {/if}
</div>

<style>
  .no-items {
    font-size: 20px;
    text-align: center;
  }
  
  .sorting-item {
    display: flex;
    align-items: center;
    padding: 1px 17px 1px 3px;
    font-size: 12px;
    font-weight: 700;
    color: #6e6e6e;
    white-space: nowrap;
    border: 2px solid #6e6e6e;
    border-radius: 12px;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .sorting-item span {
    display: inline-block;
    vertical-align: middle;
    font-weight: 700;
    line-height: 16px;
  }

  .sorting-item:hover,
  .sorting-item.is-active {
    color: #fff;
    background-color: #6e6e6e;
  }

  .sorting-row .sorting-arrow {
    display: inline-block;
    vertical-align: middle;
    visibility: hidden;
  }

  .sorting-row.sorted-by-asc .sorting-arrow {
    transform: rotate(180deg);
  }

  .sorting-item.is-active .sorting-arrow {
    visibility: visible;
  }

  .data-list {
    display: table;
    width: 100%;
    padding-left: 0;
    border-spacing: 0 10px;
    list-style: none;
  }

  .data-list .data-item {
    display: table-row;
    padding: 16px;
    margin-top: 12px;
    background: #fff;
    box-shadow:
      rgba(0, 0, 0, 0.1) 0px 1px 3px 0px,
      rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;
    box-sizing: border-box;
    cursor: pointer;
  }

  .data-list .data-item-header {
    cursor: default;
    box-shadow: none;
    background-color: transparent;
  }

  .data-list .data-column {
    display: table-cell;
    padding: 16px;
  }

  .data-list .data-column-label {
    display: block;
    font-weight: 700;
  }

  .data-list .data-item-title {
    margin: 10px 0 0;
    font-weight: 700;
    font-size: 18px;
  }

  .data-list .data-column-data {
    display: block;
    margin-top: 10px;
    font-size: 16px;
  }
</style>
