
- If you send data in the **path parameter**, FastAPI **automatically extracts it** and provides it to your function — for **any HTTP method** (`GET`, `POST`, `PUT`, `DELETE`, etc.)

1. Pydantic model + POST
```python
class Note(BaseModel):
    title: str
    content: str

@app.post("/note")
def create_note(note: Note):
    return {"msg": "note received", "data": note}
```

2. pydantic model + delete

```python
@app.delete("/note")
def delete_note(note: Note):  # ❌ won't work
    ...
```

correct way

```python
@app.delete("/note")
def delete_note(note: Note = Body(...)):
    return note
```

3. No pydanctic + POST

```python
@app.post("/note")
def create_note(title: str, content: str):
    return {"title": title, "content": content}

# works if 
POST /note?title=hi&content=test

# JSON body not work unless specified 

@app.post("/note")
def create_note(
    title: str = Body(...),
    content: str = Body(...)
):
..
```

4. No pydanctic + DELETE REQUEST

```python
@app.delete("/note")
def delete_note(note_id: int):  # query param
    return {"deleted": note_id}
    
# work if 
DELETE /note?note_id=5

```