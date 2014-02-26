#==========================================================================
# Copyright 2012 Lucidel, Inc., 2013 Cloudoscope Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this work except in compliance with the License.
# You may obtain a copy of the License in the LICENSE file, or at:
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#==========================================================================

In order to run the example, please follow the next steps
1. Clone the repository
2. within the installation tree create a soft link from directory moma_django into moma_example/moma_django
3. Dependencies:
3.1 Make sure that you have mongodb installed and running (version 2.0.2)
3.2 Make sure that you have the following python modules installed: pymongo, bson, djangotoolbox (0.9.2)
4. Create the database
   ./manage.py syncdb
   Define an admin user in the process of the database creation

Run testing

5. Run tests:
   ./manage.py test testing
   Once the tests pass, you can validate that certain collections were created within mongodb. Use mongo console:
   show dbs;
   to validate that "test_momaexample" was created. Use that db:
   use test_momaexample;
   and validate that there are certain collections:
   show collections;
   This would produce testing_testmodel1, testing_testmodel2, testing_testmodel2, test_uniquevisit. Check the content using:
   db.testing_uniquevisit.find({"location.cr":"South Africa"})
   to get a single record of a visitor from South Africa, or visitor from New York city:
   db.testing_uniquevisit.find({"location.ct":"New York"})

6. Run the example:
   ./manage.py runserver 8000
   Once connected to http://localhost:8000/ you can register, login add questions with media, vote for questions and
   review questions
