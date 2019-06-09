FROM ruby

# ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update \
 && apt-get install -y nodejs \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

RUN mkdir /app
WORKDIR /app
RUN gem install nokogiri -v 1.10.3 \
&& gem install sassc -v 2.0.1 \
&& gem install puma -v 3.12.1 \
&& gem install pg -v 1.1.4 \
&& gem install ffi -v 1.11.1 \
&& gem install byebug -v 11.0.1 \
&& gem install bindex -v 0.7.0 \
&& gem install websocket-driver -v 0.6.5 \
&& gem install nio4r -v 2.3.1

COPY Gemfile /app
COPY Gemfile.lock /app
RUN bundle install

COPY . /app

EXPOSE 8080

CMD ["bin/rails", "s", "-b", "0.0.0.0", "-p", "8080", "-e", "development"]
