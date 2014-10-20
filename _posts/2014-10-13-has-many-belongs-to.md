---
layout: post
title: Class Relationships
---

### Has Many and Belongs To

There is a relationship we can define between classes in ruby which makes it
very easy to communicate between objects in rails.  If we decide to have an
application which has a Gallery model and an Image model ( *Note classes are
singular, controllers are plural* ), we can relate the two simply by using the
code below:

<pre><code>
class Gallery < ActiveRecord::Base
  has_many :images
end

class Image < ActiverRecord::Base
  belongs_to :gallery
end
</code></pre>

Pluralizing classes is important when using these connections with another
model.  It also helps to draw an ERD (Entity Relationship Diagram) to help
decide whether you need these connections.  It makes it easier to see a solution to a problem.


