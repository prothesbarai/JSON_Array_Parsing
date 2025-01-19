# JSON Array Parsing

JSON Array Parsing With Volley Library


## Implementation

implementation on your project

#### Step 1 : 

```bash
    dependencies {

        implementation 'com.android.volley:volley:1.2.1'

    }
```


#### Step 2 : ---------------------------- [ When Parsing With Static Index Number ]

```java
    JsonArrayRequest jsonArrayRequest =new JsonArrayRequest(Request.Method.GET, url, null, new Response.Listener<JSONArray>() {
            @Override
            public void onResponse(JSONArray response) {
                try {
                    JSONObject jsonObject = response.getJSONObject(1); // Here 1 is index number of array
                    String title = jsonObject.getString("title");
                    String description = jsonObject.getString("description");
                    String id = jsonObject.getString("id");
                    String url = jsonObject.getString("url");
                    textView.setText(""+title+"\n"+description+"\n"+id+"\n"+url);
                } catch (JSONException e) {
                    throw new RuntimeException(e);
                }
            }
        }, new Response.ErrorListener() {
            @Override
            public void onErrorResponse(VolleyError error) {
                Toast.makeText(MainActivity.this, "Error", Toast.LENGTH_SHORT).show();
            }
        });

        RequestQueue requestQueue = Volley.newRequestQueue(MainActivity.this);
        requestQueue.add(jsonArrayRequest);
```


## OR,      [ Using For Loop ]


#### Step 2 : ---------------------------- [ When Parsing With Dynamic Index Number With For Loop]

```java
    JsonArrayRequest jsonArrayRequest =new JsonArrayRequest(Request.Method.GET, url, null, new Response.Listener<JSONArray>() {
            @Override
            public void onResponse(JSONArray response) {
                try {

                    for (int i=0; i<response.length(); i++){
                        JSONObject jsonObject = response.getJSONObject(i);
                        String title = jsonObject.getString("title");
                        String description = jsonObject.getString("description");
                        String id = jsonObject.getString("id");
                        String url = jsonObject.getString("url");
                        textView.append(""+title+"\n"+description+"\n"+id+"\n"+url+"\n\n");
                    }

                } catch (JSONException e) {
                    throw new RuntimeException(e);
                }
            }
        }, new Response.ErrorListener() {
            @Override
            public void onErrorResponse(VolleyError error) {
                Toast.makeText(MainActivity.this, "Error", Toast.LENGTH_SHORT).show();
            }
        });

        RequestQueue requestQueue = Volley.newRequestQueue(MainActivity.this);
        requestQueue.add(jsonArrayRequest);
```
## Author

- [Prothes Barai](https://prothes-asp.github.io/prothes/)

