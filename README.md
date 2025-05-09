{
    "Portfolio": "Enterprise Digital Transformation",
    "Application": "PEGA Claims Processing",
    "product": {
        "name": "PEGA-WebServices",
        "description": "",
        "RunEnv": "OnPrem",
        "dependency_auth": {
            "auth_pattern": "pega-authentication-pattern",
            "payload": {
                "userid": "${USERID}",
                "password": "${PASSWORD}"
            }
			"credentials": {
                "x-ibm-client-id": "${ENV_CLIENT_ID}",
                "x-ibm-client-secret": "${ENV_CLIENT_SECRET}"
            }
        },
		"api_headers": {
            "static": {
                "content_type": "application/json",
                "accept": "application/json",
                "Cookie": "session_id=abc123xyz"
            },
            "dynamic": {
                "tag1": "${CUSTOM_GENERATE_SEQNUM}",
                "tag2": "${CUSTOM_GENERATE_TIMESTAMP}"
            }
        },
        "api_auth": {
            "static": {
                "content_type": "application/json",
                "accept": "application/json",
                "Cookie": "session_id=abc123xyz"
            },
            "dynamic": {
                "tag1": "${CUSTOM_GENERATE_SEQNUM}",
                "tag2": "${CUSTOM_GENERATE_TIMESTAMP}"
            }
        },
        "database": {
            "primary": "Facets",
            "secondary": "SnowFlake"
        },
        "base_url": {
            "Dev": "http://dev.api.example.com",
            "Test": "http://test.api.example.com",
            "Stage": "http://stage.api.example.com"
        },
      },
    "reporting": {
        "maintainers": [
            {
                "name": "Chandra Sarikonda",
                "email": "chandra.sarikonda@blueshieldca.com"
            },
            {
                "name": "DevX Team",
                "email": "devx-testautomationframework-fte@blueshieldca.com"
            }
        ],
        "BB": {
            "url": "https://bitbucket.org/blueshieldca/shieldadvisorwebservices/src/master/"
        },
        "ConfluencePage": "https://docs.example.com/api",
    }
}


Service JSON

{
    "product": "PEGA-WebServices",
    "Feature": "PEGA-WebServices",
    "service": {
        "api_name": "/ServiceName",
        "api_shortName": "",
        "api_URL": "",
        "api_UrlPath": "",
        "api_RequestType": "",
        "api_version": "v1",
        "api_Json": "jsonfilename",
        "api_data_payloads": {
            "memberid": {
                "path": "jmep path",
                "default": "value",
                "feature": "HMOMember"
            },
            "DOB": {
                "path": "jmep path",
                "default": "value",
                "feature": "DOBAll"
            }
        },
        "data_response": {
            "MemberName": {
                "path": "jmep path"
            },
            "Age": {
                "path": "jmep path"
            }
        },
        "api_performance": {
            "api_responseTimeSLA": "2000",
            "api_volumePerHour": ""
        },
        "api_repo": {
			"ConfluencePage": "https://docs.example.com/api",
            "BitBucketRepo": "https://bitbucket.org/blueshieldca/shieldadvisorwebservices/src/master/",
            "TestRepo": "https://testrepo.example.com/project"
        }
    }
}
