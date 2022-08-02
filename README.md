import json
import pandas as pd
import requests

#pip install wordsmith

from wordsmith import Wordsmith

ws = Wordsmith('53bd974ee822b0dd6d69e639e9d11b15dae9f72589ada1bc22776b2ebac96203')
# Be careful as this returns a list (since Wordsmith allows duplicate project names)
matches = ws.find_project('S&P Narrative')

matches

def fetch_symbol_narrative_from_ws(json_data):
    
    print("Fetching quotes narrative for portfolio: " + json_data['data']['shortName'] + " from Wordsmith...")
    
    ws_headers = {
        'Authorization': '53bd974ee822b0dd6d69e639e9d11b15dae9f72589ada1bc22776b2ebac96203',
        'Content-type': 'application/json'
    }

    ws_endpoint = "https://api.automatedinsights.com/v1/projects/iexcloud/templates/focus_2/outputs"

    http_req = {'url': ws_endpoint,
                'headers': ws_headers,
                'json': json_data}

    request = requests.post(**http_req)

    response_content = json.loads(request.content)
    
    nlg = response_content['data']['content']

    return nlg
    
    
    
    def fetch_symbol_narrative_from_ws(json_data):
    
    print("Fetching quotes narrative for portfolio: " + json_data['data']['shortName'] + " from Wordsmith...")
    
    ws_headers = {
        'Authorization': 'Bearer b1d1c046bd712882797e65734921af22a6aa09f323b6fa93718940561fc00d41',
        'Content-type': 'application/json'
    }

    ws_endpoint = "https://api.automatedinsights.com/v1/projects/iexcloud/templates/focus_2/outputs"

    http_req = {'url': ws_endpoint,
                'headers': ws_headers,
                'json': json_data}

    request = requests.post(**http_req)

    response_content = json.loads(request.content)
    
    nlg = response_content['data']['content']

    return nlg
