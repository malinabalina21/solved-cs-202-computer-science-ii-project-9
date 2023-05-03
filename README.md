Download Link: https://assignmentchef.com/product/solved-cs-202-computer-science-ii-project-9
<br>



<strong> </strong>

<strong>  </strong>




<strong>Objectives:  </strong>The main objectives of this project are to test your ability to create and use queuebased dynamic data structures. A review of your knowledge to manipulate dynamic memory, classes, pointers and iostream to all extents, is also included. You may from now on freely use <strong>square bracket</strong>-indexing, <strong>pointers</strong>, <strong>references</strong>, all <strong>operators</strong>, the <strong>&lt;cstring&gt;</strong> library, and the <strong>std::string</strong> type as you deem proper.




<strong>Description: </strong>

For this project you will create a Queue class, both an Array-based and a Node-based variant. A Queue is a First In First Out (FIFO) data structure. A Queue exclusively inserts data at the back (<strong>push</strong>) and removes data from the front (<strong>pop</strong>). The Queue’s <strong>front</strong> data member points to the first inserted element (the front one), and the <strong>back</strong> data member points to the last (the rear one).




<strong>Array-based Queue: </strong>

The following ArrayQueue.h file extract is used to explain the required specifications for the class (it implements a Queue handling DataType objects):




<strong>const size_t ARRAY_MAX = 1000; </strong>

<strong> </strong>

<strong>class ArrayQueue{ </strong>

<strong> </strong>

<strong>  friend std::ostream&amp; operator&lt;&lt;(std::ostream&amp; os,               //(i) </strong>

<strong>                                const ArrayQueue&amp; arrayQueue);  </strong>

<strong> </strong><strong>  public: </strong>

<strong>    ArrayQueue();                                              //(1) </strong>

<table width="629">

 <tbody>

  <tr>

   <td width="576"><strong>    ArrayQueue(size_t count, const DataType&amp; value);         </strong></td>

   <td width="53"><strong>//(2) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    ArrayQueue(const ArrayQueue&amp; other);                    </strong></td>

   <td width="53"><strong>//(3) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    ~ArrayQueue();                                        </strong><strong> </strong></td>

   <td width="53"><strong>//(4) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    ArrayQueue&amp; operator= (const ArrayQueue&amp; rhs);           </strong></td>

   <td width="53"><strong>//(5) </strong></td>

  </tr>

 </tbody>

</table>

<strong>     </strong>

<table width="633">

 <tbody>

  <tr>

   <td width="384"><strong>    DataType&amp; front();                </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>                 //(6a) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    const DataType&amp; front() const;     </strong><strong>    </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(6b) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    DataType&amp; back();                 </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(7a) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    const DataType&amp; back() const;      </strong><strong>                 </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(7b) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void push(const DataType&amp; value);  </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(8) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void pop();                        </strong><strong>                 </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(9) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    size_t size() const;               </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>                 //(10) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    bool empty() const;               </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(11) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    bool full() const;                </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(12) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void clear();                     </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(13)  </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void serialize(std::ostream&amp; os);  </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(14)  </strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>  private: </strong>

<strong>    DataType m_array[ARRAY_MAX];     size_t m_front;     size_t m_back;     size_t m_size; </strong>

<strong>}; </strong>




The <strong>ArrayQueue </strong>Class will contain the following<strong> private </strong>data members:

<ul>

 <li><strong>m_array,</strong> the array that holds the data. <em>Note</em>: This is a Statically Allocated array that holds ARRAY_MAX number of objects, be careful <em>not</em> to treat is as a Dynamically Allocated one.</li>

 <li><strong>m_size</strong>, a size_t, keeps track of how many elements are currently stored in the Queue (and therefore considered valid). <em>Note</em>: This cannot exceed ARRAY_MAX.</li>

 <li><strong>m_front,</strong> a size_t, with the respective m_array index of the front element of the Queue.</li>

 <li><strong>m_back</strong>, a size_t, with the respective m_array index of the back element of the Queue.</li>

</ul>

<strong>,</strong>will have the following<strong> public </strong>member functions:

<ul>

 <li><strong>(1) Default Constructor</strong> – will instantiate a new Queue object with no valid data.</li>

 <li><strong>(2) Parametrized Constructor </strong>– will instantiate a new Queue object, which will hold size_t count number of elements in total, all of them initialized to be equal to the parameter value.</li>

 <li><strong>(3) Copy Constructor</strong> – will instantiate a new Queue object which will be a separate copy of the data of the <strong>other </strong>Queue object which is getting copied. <em>Note</em>: Consider whether you actually need to implement this.</li>

 <li><strong>(4) Destructor </strong>– will destroy the instance of the Queue object. <em>Note</em>: Consider whether you actually need to implement this.</li>

 <li><strong>(5) operator= </strong>will assign a new value to the calling Queue object, which will be an exact copy of the rhs object passed as a parameter. Returns a reference to the calling object to be used for cascading operator= as per standard practice. <em>Note</em>: Consider whether you actually need to implement this.</li>

 <li><strong>(6a,6b) front </strong>returns a Reference to the front element of the Queue. <em>Note</em>: Since it returns a</li>

</ul>

Reference, before calling this method the user must ensure that the Queue is not empty.

<ul>

 <li><strong>(7a,7b) back </strong>returns a Reference to the back element of the Queue. <em>Note</em>: Since it returns a</li>

</ul>

Reference, before calling this method the user must ensure that the Queue is not empty.

<ul>

 <li><strong>(8) push </strong>inserts at the back of the Queue an element of the given value. <em>Note</em>: Since m_size can never exceed ARRAY_MAXSIZE, checking if the Queue is full prior to pushing a new element makes sense.</li>

 <li><strong>(9) pop </strong>removes from the front element of the Queue. <em>Note</em>: Since m_size is an unsigned value, checking if the Queue is empty prior to popping an element makes sense.</li>

 <li><strong>(10) size </strong>will return the size of the current Queue.</li>

 <li><strong>(11) empty </strong>will return a bool, true if the Queue is empty (m_size==0).</li>

 <li><strong>(12) full </strong>will return a bool, true if the Queue is full (m_size==ARRAY_MAXSIZE).</li>

 <li><strong>(13) clear </strong>performs the necessary actions, so that after its call the Queue will be semantically considered empty.</li>

 <li><strong>(14) serialize </strong>outputs to the parameter ostream os the complete content of the calling Queue object.</li>

</ul>

as well as a non-member overload for:

<ul>

 <li><strong>(i) operator&lt;&lt; </strong>will output (to terminal or file) the complete content of the arrayQueue object passed as a parameter.</li>

</ul>




<strong>Final Note about Array-based Queue: </strong>

The required implementation will be a wrap-around Queue. This means that:

<ol>

 <li>Pushing an element will move the back by one (m_back = (m_back+1) %</li>

</ol>

ARRAY_MAXSIZE) as seen in Lecture 20 and increment the m_size by 1.

<ol>

 <li>Popping an element will move the front by one (m_front = (m_front+1) % ARRAY_MAXSIZE) as seen in Lecture 20 and decrement the m_size by 1.</li>

 <li>Keeping track of the count of elements in the Queue (through m_size) as seen in Lecture 20 is necessary.</li>

</ol>




<strong> </strong>

<strong> </strong>

<strong>Node-based Queue: </strong>

The following NodeQueue.h file extract is used to explain the required specifications for the class (the corresponding Node class handles DataType objects, as per your previous Project) :




<strong>class NodeQueue{ </strong>

<strong> </strong>

<table width="629">

 <tbody>

  <tr>

   <td width="576"><strong>  friend std::ostream&amp; operator&lt;&lt;(std::ostream&amp; os,                             const NodeQueue&amp; nodeQueue);  </strong><strong> </strong><strong>  public: </strong></td>

   <td width="53"><strong>//(i) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    NodeQueue();                                          </strong></td>

   <td width="53"><strong>//(1) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    NodeQueue(size_t size, const DataType&amp; value);          </strong></td>

   <td width="53"><strong>//(2) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    NodeQueue(const NodeQueue&amp; other);                      </strong></td>

   <td width="53"><strong>//(3) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    ~NodeQueue();                                          </strong><strong> </strong></td>

   <td width="53"><strong>//(4) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    NodeQueue&amp; operator= (const NodeQueue&amp; rhs);             </strong></td>

   <td width="53"><strong>//(5) </strong></td>

  </tr>

 </tbody>

</table>

<strong>     </strong>

<table width="633">

 <tbody>

  <tr>

   <td width="384"><strong>    DataType&amp; front();                </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>                 //(6a) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    const DataType&amp; front() const;     </strong><strong>    </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(6b) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    DataType&amp; back();                 </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(7a) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    const DataType&amp; back() const;      </strong><strong>                 </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(7b) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void push(const DataType&amp; value);  </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(8) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void pop();                        </strong><strong>                 </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>               //(9) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    size_t size() const;               </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(10) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    bool empty() const;               </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(11) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    bool full() const;                </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(12) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void clear();                     </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(13) </strong></td>

  </tr>

  <tr>

   <td width="384"><strong>    void serialize(std::ostream&amp; os);  </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="201"><strong>              //(14)  </strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong><strong>  private: </strong>

<strong> </strong>

<strong>    Node *m_front; </strong>

<strong>    Node *m_back; </strong>

<strong>}; </strong>




The <strong>NodeQueue </strong>Class will contain the following<strong> private </strong>data members:

<ul>

 <li><strong>m_front,</strong> a Node Pointer type, pointing to the front element of the Queue.</li>

 <li><strong>m_back</strong>, a Node Pointer type, pointing to the back element of the Queue.</li>

</ul>

<strong>,</strong>will have the following<strong> public </strong>member functions:

<ul>

 <li><strong>(1) Default Constructor</strong> – will instantiate a new Queue object with no elements (Nodes).</li>

 <li><strong>(2) Parametrized Constructor </strong>– will instantiate a new Queue object, which will dynamically allocate at instantiation to hold size_t count number of elements (Nodes), all of them initialized to be equal to the parameter value.</li>

 <li><strong>(3) Copy Constructor</strong> – will instantiate a new Queue object which will be a separate copy of the data of the <strong>other </strong>Queue object which is getting copied. <em>Note</em>: Consider why now you do need to implement this.</li>

 <li><strong>(4) Destructor </strong>– will destroy the instance of the Queue object. <em>Note</em>: Consider why now you do need to implement this.</li>

 <li><strong>(5) operator= </strong>will assign a new value to the calling Queue object, which will be an exact copy of the rhs object passed as a parameter. Returns a reference to the calling object to be used for cascading operator= as per standard practice. <em>Note</em>: Consider why now you do need to implement this.</li>

 <li><strong>(6a,6b) front </strong>returns a Reference to the front element of the Queue. <em>Note</em>: Since it returns a</li>

</ul>

Reference, before calling this method the user must ensure that the Queue is not empty.

<ul>

 <li><strong>(7a,7b) back </strong>returns a Reference to the back element of the Queue. <em>Note</em>: Since it returns a</li>

</ul>

Reference, before calling this method the user must ensure that the Queue is not empty.

<ul>

 <li><strong>(8) push </strong>inserts at the back of the Queue an element of the given value. <em>Note</em>: No imposed maximum size limitations exist for the Node-based Queue variant.</li>

 <li><strong>(9) pop </strong>removes from the front element of the Queue. <em>Note</em>: Checking if the Queue is empty prior to popping an element makes sense.</li>

 <li><strong>(10) size </strong>will return the size of the current Queue.</li>

 <li><strong>(11) empty </strong>will return a bool, true if the Queue is empty.</li>

 <li><strong>(12) full </strong>will return a bool, true if the Queue is full. <em>Note</em>: Kept for compatibility, should always return false.</li>

 <li><strong>(13) clear </strong>performs the necessary actions, so that after its call the Queue will be empty.</li>

</ul>

<em>Note</em>: Consider now how you will implement this in contrast to the other queue variant.

<ul>

 <li><strong>(14) serialize </strong>outputs to the parameter ostream os the complete content of the calling Queue object.</li>

</ul>

as well as a non-member overload for:

<ul>

 <li><strong>(i) operator&lt;&lt; </strong>will output (to terminal or file) the complete content of the nodeQueue object passed as a parameter.</li>

</ul>




<strong>Final Note about Node-based Queue: </strong>

The required implementation will be a linear linked-list. This means that:

<ol start="20">

 <li>It will have a front pointer to the first element of the Queue, as seen in Lecture 20.</li>

 <li>It will have a back pointer to the last element of the Queue, as seen in Lecture 20.</li>

 <li>You may modify the specifications to add an auxiliary variable to keep track of the count of elements in the Queue (e.g. an size_t m_size) if you so wish.</li>

</ol>




You will create the necessary ArrayQueue.h and NodeQueue.h files that contain the necessary class declarations and implementations. You should also create a source file proj9.cpp which will be a test driver for your classes.




<strong>The completed project should have the following properties: </strong> Ø Written, compiled and tested using Linux.

<ul>

 <li>It must compile successfully on the department machines using Makefile(s), which will be invoking the g++ compiler. Instructions how to remotely connect to department machines are included in the Projects folder in WebCampus.</li>

 <li>The code must be commented and indented properly.</li>

</ul>

Header comments are required on all files and recommended for the rest of the program. Descriptions of functions commented properly.

<ul>

 <li>A one page (minimum) typed sheet documenting your code. This should include the overall purpose of the program, your design, problems (if any), and any changes you would make given more time.</li>

</ul>

<strong> </strong>

<strong>Turn in:</strong> Compressed Header &amp; Source files, Makefile(s), and project documentation.




<strong>Submission Instructions: </strong>

<ul>

 <li>You will submit your work via WebCampus</li>

 <li>Name your code file proj9.cpp</li>

 <li>If you have header file, name it proj9.h</li>

 <li>If you have class header and source files, name them as the respective class (ArrayQueue.h NodeQueue.h) This source code structure is not mandatory, but advised.</li>

 <li>Compress your:

  <ol>

   <li>Source code</li>

   <li>Makefile(s)</li>

   <li>Documentation Do not include executable  Ø Name the compressed folder:</li>

  </ol></li>

</ul>

PA#_Lastname_Firstname.zip

Ex: PA9_Smith_John.zip







<strong>Late Submission:</strong>

A project submission is “late” if any of the submitted files are time-stamped after the due date and time. Projects will be accepted up to 24 hours late, with 20% penalty.

















