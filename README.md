
# App.js

 
```bash
import 'bootstrap/dist/css/bootstrap.min.css';
import { useRef, useState } from 'react';
function App() {
  const inputRef = useRef();
  const items = [
    'Apple',
    'Pinapple',
    'Watermalone',
    'Graphs',
    'Guavava',
    'Lemon'
  ]
  const [filterValue, setFilterValue] = useState(items)

  const handleChange = (e) => {
    const filter = items.filter((item) => (
      // item.toLowerCase().indexOf(e.target.value.toLowerCase())!==-1 
      item.toLowerCase().includes(e.target.value.toLowerCase())
    ));
    setFilterValue(filter);
  }
  const handleClear = (e) => {
    setFilterValue(items);
    inputRef.current.value = '';
  }
  return (
    <div className='mt-5'>
      <div className='container d-flex flex-column w-50 h-100'>
        <div className='card shadow '>
          <div className='card-title '>
            <h2 className='text-center m-2 fw-bold'>Search Functionality</h2>

          </div>

          <div className='card-body'>
            <input ref={inputRef} name='search' placeholder='search here...' className='form-control' onChange={handleChange} />
            <div className='d-flex justify-content-between mt-2'>
              <small className='text-end'>Fetch <strong>{filterValue.length}</strong> record(s) out of <strong>{items.length}</strong></small>
              <button className='btn btn-primary btn-sm fw-bold' disabled={filterValue.length !== 0} onClick={handleClear}>Clear</button>
            </div>
            <div className='text-center fw-bold'>
              {filterValue.length === 0 ? (
                <div>No Record found</div>
              ) : (
                filterValue.map((filtered, index) => (
                  <div key={index}>{filtered}</div>
                ))
              )}
              {/* {filterValue && filterValue.map((filtred)=>(
                  <div>{filtred}</div>
                ))}
                 {filterValue.length === 0 && <div>No Record found</div>}  */}
            </div>
          </div>
        </div>
      </div>
    </div>
  )
}

export default App;


```

